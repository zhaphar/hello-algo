# 小结

- 动态规划通过将原问题分解为子问题来求解问题，并通过存储子问题的解来规避重复计算，实现高效的计算效率。子问题分解是一种通用的算法思路，在分治、动态规划、回溯中具有不同的性质。
- 不考虑时间的前提下，所有动态规划问题都可以用回溯（暴力搜索）进行求解，但递归树中存在大量的重叠子问题，效率极低。通过引入记忆化列表，可以存储所有计算过的子问题的解，从而保证重叠子问题只被计算一次。
- 记忆化递归是一种从顶至底的递归式解法，而与之对应的动态规划是一种从底至顶的递推式解法，就像是在“填写表格”一样。由于当前状态仅依赖于某些局部状态，因此我们可以消除 $dp$ 表的一个维度，从而降低空间复杂度。
- 动态规划问题的三大特性：重叠子问题、最优子结构、无后效性。如果原问题的最优解可以从子问题的最优解构建得来，则此问题就具有最优子结构。无后效性指对于一个状态，其未来发展只与该状态有关，与其所经历的过去的所有状态无关。许多组合优化问题都不具有无后效性，无法使用动态规划快速求解。
- 背包问题是最典型的动态规划题目，具有 0-1 背包、完全背包、多重背包等变种问题。
- 0-1 背包的状态定义为前 $i$ 个物品在剩余容量为 $c$ 的背包中的最大价值。这是一种常见的定义方式。不放入物品 $i$ ，状态转移至 $[i-1, c]$ ，放入则转移至 $[i-1, c-wgt[i-1]]$ ，由此便得到最优子结构，并构建出状态转移方程。对于状态压缩，由于每个状态依赖正上方和左上方的状态，因此需要倒序遍历列表，避免左上方状态被覆盖。
- 完全背包的每种物品有无数个，因此在放置物品 $i$ 后，状态转移至 $[i, c-wgt[i-1]]$ 。由于状态依赖于正上方和正左方的状态，因此状态压缩后应该正序遍历。
- 零钱兑换问题是完全背包的一个变种。为从求“最大“价值变为求“最小”硬币数量，我们将状态转移方程中的 $\max()$ 改为 $\min()$ 。为从求“不超过”背包容量到求“恰好”凑出目标金额，我们使用 $amt + 1$ 来表示“无法凑出目标金额”的无效解。
- 零钱兑换 II 问题从求“最少硬币数量”改为求“硬币组合数量”，状态转移方程相应地从 $\min()$ 改为求和运算符。
- 编辑距离（Levenshtein 距离）用于衡量两个字符串之间的相似度，定义为从一个字符串到另一个字符串的最小编辑步数，编辑操作包括添加、删除、替换。
- 编辑距离问题的状态定义为将 $s$ 的前 $i$ 个字符更改为 $t$ 的前 $j$ 个字符所需的最少编辑步数。考虑字符 $s[i]$ 和 $t[j]$ ，具有三种决策：在 $s[i-1]$ 之后添加 $t[j-1]$ 、删除 $s[i-1]$ 、将 $s[i-1]$ 替换为 $t[j-1]$ ，它们都有相应的剩余子问题，据此就可以找出最优子结构与构建状态转移方程。值得注意的是，当 $s[i] = t[j]$ 时，无需编辑当前字符，直接跳过即可。
- 在编辑距离中，状态依赖于其正上方、正左方、左上方的状态，因此状态压缩后正序或倒序遍历都无法正确地进行状态转移。利用一个变量暂存左上方状态，即转化至完全背包地情况，可以在状态压缩后使用正序遍历。
