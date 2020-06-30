# usage-summary
python
# 位运算
位运算是指二进制进行的加减，与，或，异或，同或，移位等运算。
位运算一般是对整数做一些运算，得到相关结果。可以指定二进制中的某位进行运算。
## 统计整数变换为二进制后1的个数
 思路：根据运算技巧，某个二进制与其减去1之后的数相与，就等价于将二进制的最后一位1去掉，
 因此可以利用此特点，计算将二进制数变为0之后与的次数即可。
 
     def a(n:int):
         count=0
         while n!=0:
            n=n & (n-1)
            count+=1
     return count

## 计算汉明距离
 汉明距离是指两个数字中对应位数不同的个数。
 
 思路：利用异或，不同位数异或会变为1，计算1 的位数即可的到结果
 
      def hanmingDistance(x:int,y:int):
        a=x^y
        count=0
        while a!=0:
            a=a&(a-1)
            count+=1
        return count
        
## 计算数组中只出现一次的数（其他数均出现两次）
 思路：两个相同的数异或为0，而0与任何数异或均为此数本身
 
        from typing import List
        def singleNumber(nums:List):
        res=0
        for i in nums:
            res=res^i
        return res
 
## 计算一个数组中任意两个数之间的汉明距离的总和
 思路：核心算法为，（排列组合计算），取每个数的相同位数，统计0的个数与1的个数，
 两者个数相乘，即为汉明距离。将32位全部循环一次，就可以得到结果
 
    from typing import List
    def sumhanmingDistance(nums:List):
        res=0
        for i in range(32):#一个整数32位
            count_0=0
            count_1=0
            for j in range(len(nums)):
                if(nums[j]>>i)&1:#向右移位，将数组中每个数的每个位同时提取出来
                    count_1+=1
                else:
                    count_0+=1
            res=res+count_0*count_1#简便算法，他俩的乘积就是排列组合的和的结果（将每个数的同一位进行排列组合，最终即可得到汉明距离）
        return res
 
 
 
 
