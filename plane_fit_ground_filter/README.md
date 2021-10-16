### 地面平面拟合
1.0 种子点集的选取
 -  首先选取一个种子点集(seed point set)，这些种子点来源于点云中高度（即z值）较小的点，种子点集被用于建立描述地面的初始平面模型，那么如何选取这个种子点集呢？我们引入最低点代表（Lowest Point Representative, LPR）的概念。LPR就是num_lpr_个最低高度点的平均值，LPR保证了平面拟合阶段不受测量噪声的影响。
 -  输入是一个点云，这个点云内的点已经沿着z方向（即高度）做了排序，取 num_lpr_ 个最小点，求得高度平均值 lpr_height（即LPR），选取高度小于 lpr_height + th_seeds_的点作为种子点。 

2.0 平面模型
 -  点云中的点到这个平面的正交投影距离小于阈值Thdist则认为该点属于地面，否则属于非地面