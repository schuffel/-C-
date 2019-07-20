# C++语法个人小结

~~~~~~~~~~~~~~~~~~~~~~~第一天打卡
explicit:
------
在C++中explicit关键字被用于修饰类的构造函数，被修饰的构造函数不能发生隐式转换，只能以显示的方式进行
class Circle  
 {  
public:  
     explicit Circle(double r) : R(r) {}  
     explicit Circle(int x, int y = 0) : X(x), Y(y) {}  
     explicit Circle(const Circle& c) : R(c.R), X(c.X), Y(c.Y) {}  
private:  
     double R;  
     int    X;  
     int    Y;  
};  
   
int _tmain(int argc, _TCHAR* argv[])  
{  
 //一下3句，都会报错  
    //Circle A = 1.23;   
    //Circle B = 123;  
    //Circle C = A;  
       
 //只能用显示的方式调用了  
 //未给拷贝构造函数加explicit之前可以这样  
         Circle A = Circle(1.23);  
         Circle B = Circle(123);  
         Circle C = A;  
   
//给拷贝构造函数加了explicit后只能这样了  
        Circle A(1.23);  
        Circle B(123);  
        Circle C(A);  
    return 0;  
} 
