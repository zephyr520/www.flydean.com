AI数学基础之:奇异值和奇异值分解

[toc]

# 简介

奇异值是矩阵中的一个非常重要的概念，一般是通过奇异值分解的方法来得到的，奇异值分解是线性代数和矩阵论中一种重要的矩阵分解法，在统计学和信号处理中非常的重要。

在了解奇异值之前，让我们先来看看特征值的概念。

# 相似矩阵

在线性代数中，相似矩阵是指存在相似关系的矩阵。设A，B为n阶矩阵，如果有n阶可逆矩阵P存在，使得P<sup>-1</sup>AP=B，则称矩阵A与B相似，记为A~B。

# 对角矩阵

对角矩阵(diagonal matrix)是一个主对角线之外的元素皆为0的矩阵，常写为diag（a1，a2,...,an) 。对角矩阵可以认为是矩阵中最简单的一种，值得一提的是：对角线上的元素可以为 0 或其他值，对角线上元素相等的对角矩阵称为**数量矩阵**；对角线上元素全为1的对角矩阵称为**单位矩阵**。对角矩阵的运算包括和、差运算、数乘运算、同阶对角阵的乘积运算，且结果仍为对角阵。

# 可对角化矩阵

可对角化矩阵是线性代数和矩阵论中重要的一类矩阵。如果一个方块矩阵 A 相似于对角矩阵，也就是说，如果存在一个可逆矩阵 P 使得 P <sup>−1</sup>AP 是对角矩阵，则它就被称为可对角化的。

# 特征值

设A为n阶矩阵，若存在常数λ及n维非零向量x，使得Ax=λx，则称λ是矩阵A的特征值，x是A属于特征值λ的特征向量。 

一个矩阵的一组特征向量是一组正交向量。

即特征向量被施以线性变换 A 只会使向量伸长或缩短而其方向不被改变。

一个线性变换通常可以由其特征值和特征向量完全描述。特征空间是相同特征值的特征向量的集合。

# 特征分解

特征分解（Eigendecomposition），又称谱分解（Spectral decomposition）是将矩阵分解为由其特征值和特征向量表示的矩阵之积的方法。需要注意只有对可对角化矩阵才可以施以特征分解。

令 **A** 是一个 N×N 的方阵，且有 N 个线性无关的特征向量 q<sub>i</sub>(i=1,…,N)。这样， **A** 可以被分解为: **A= QΛQ**<sup>-1</sup>

其中 Q 是N×N方阵，且其第 i列为 A 的特征向量 。如果A的所有特征向量用x1,x2 … xm来表示的话，那么Q可以表示为：$\left[x_1,x_2,…,x_m\right]$, 其中x是n维非零向量。

 Λ 是对角矩阵，其对角线上的元素为对应的特征值，也即**Λ<sub>ii</sub>=λ<sub>i</sub>**。 也就是$\left[\begin{matrix}λ_1 … 0\\… … …\\0 … λ_m \end{matrix}\right]$



这里需要注意只有可对角化矩阵才可以作特征分解。比如 $\left[\begin{matrix}11\\01 \end{matrix}\right]$不能被对角化，也就不能特征分解。

因为 **A= QΛQ**<sup>-1</sup> ，可以看做A被分解为三个矩阵，也就是三个映射。

假如现在有一个向量x，我们可以得出下面的结论：

$Ax=QΛQ^{-1}x$

Q是正交矩阵，正交阵的逆矩阵等于其转置,所以$Q^{-1} = Q^T$.

$Q^T$对x的变换是正交变换，它将x用新的坐标系来表示，这个坐标系就是A的所有正交的特征向量构成的坐标系。比如将**x**用A的所有特征向量表示为：

$x=a_1x_1+a_2x_2+…+a_mx_m$

则通过第一个变换就可以把**x**表示为$[a_1 a_2 ... a_m]^T$。

$QΛQ^{-1}x=QΛ\left[\begin{matrix}x_1^T\\x_2^T\\…\\…\\x_m^T \end{matrix}\right](a_1x_1+a_2x_2+a_3x_3+…+a_mx_m)=QΛ\left[\begin{matrix}a_1\\a_2\\…\\a_m \end{matrix}\right]$

然后，在新的坐标系表示下，由中间那个对角矩阵对新的向量坐标换，其结果就是将向量往各个轴方向拉伸或压缩:



$QΛ\left[\begin{matrix}a_1\\a_2\\…\\a_m \end{matrix}\right]=Q\left[\begin{matrix}λ_1 … 0\\… … …\\0 … λ_m \end{matrix}\right]\left[\begin{matrix}a_1\\a_2\\…\\a_m \end{matrix}\right]=Q\left[\begin{matrix}λ_1a_1\\λ_2a_2\\…\\λ_ma_m \end{matrix}\right]$

​	如果A不是满秩的话，那么就是说对角阵的对角线上元素存在0，这时候就会导致维度退化，这样就会使映射后的向量落入m维空间的子空间中。

最后一个变换就是Q对拉伸或压缩后的向量做变换，由于Q和$Q^{-1}$是互为逆矩阵，所以Q变换是$Q^{-1}$变换的逆变换。

# 特征值的几何意义

一个矩阵乘以一个列向量相当于矩阵的列向量的线性组合。一个行向量乘以矩阵，相当于矩阵的行向量的线性组合。

所以向量乘以矩阵之后，相当于将这个向量进行了几何变换。

之前讲了 Λ 是对角矩阵，其对角线上的元素为对应的特征值，也即**Λ<sub>ii</sub>=λ<sub>i</sub>**。 也就是$\left[\begin{matrix}λ_1 … 0\\… … …\\0 … λ_m \end{matrix}\right]$

这些特征值表示的是对向量做线性变换时候，各个变换方向的变换幅度。



# 奇异值 Singular value

假如A是m * n阶矩阵，q=min(m,n)，A*A的q个非负特征值的算术平方根叫作A的奇异值。

# 奇异值分解SVD

特征值分解可以方便的提取矩阵的特征，但是前提是这个矩阵是一个方阵。如果是非方阵的情况下，就需要用到奇异值分解了。先看下奇异值分解的定义：

$A=UΣV^T$

其中A是目标要分解的m * n的矩阵，U是一个 n * n的方阵，Σ 是一个n * m 的矩阵，其非对角线上的元素都是0。$V^T$是V的转置，也是一个n * n的矩阵。

奇异值跟特征值类似，在矩阵Σ中也是从大到小排列，而且奇异值的减少特别的快，**在很多情况下，前10%甚至1%的奇异值的和就占了全部的奇异值之和的99%以上了**。也就是说，我们也可以用前r大的奇异值来近似描述矩阵。r是一个远小于m、n的数，这样就可以进行压缩矩阵。

通过奇异值分解，我们可以通过更加少量的数据来近似替代原矩阵。

> 本文已收录于 [www.flydean.com](www.flydean.com)
>
> 最通俗的解读，最深刻的干货，最简洁的教程，众多你不知道的小技巧等你来发现！
> 
> 欢迎关注我的公众号:「程序那些事」,懂技术，更懂你！
