# BT10
A1.
#include <iostream>

using namespace std;

struct Point
{
    double x;
    double y;

    Point(double _x, double _y)
    {
        x = _x; y = _y;
    }
};

void print (const Point& p1)
{
    cout << "(" << p1.x << ',' << p1.y << ')';
}

int main()
{
    Point p(2.3,4.7);
    print(p);
    return 0;
}

A2.
#include <iostream>

using namespace std;

struct Point
{
    double x;
    double y;

    Point(double _x, double _y)
    {
        x = _x; y = _y;
    }
};

void print_t_tri (const Point p1)
{
    cout << "(" << p1.x << ',' << p1.y << ')' << endl;
    cout << &p1 << endl;
}

void print_t_chieu (const Point& p2)
{
    cout << "(" << p2.x << ',' << p2.y << ')' << endl;
    cout << &p2 << endl;
}

int main()
{
    Point p(2.3,4.7);
    cout << &p << endl;
    print_t_tri(p);
    print_t_chieu(p);
    return 0;
}

A3.
#include <iostream>

using namespace std;

struct Point
{
    double x;
    double y;

    Point(double _x, double _y)
    {
        x = _x; y = _y;
    }
    Point(){}
};

Point mid_point(const Point& a, const Point& b)
{
    Point mid;
    mid.x=a.x+b.x;
    mid.y=a.y+b.y;
    return mid;
};

void print (const Point& p)
{
    cout << "(" << p.x << ',' << p.y << ')' ;
}

int main()
{
    Point a(2.3,4.7);
    Point b(4.8,2.4);
    Point c=mid_point(a,b);
    print(c);
    return 0;
}

A4.
#include <iostream>

using namespace std;

struct Point
{
    double x;
    double y;

    Point(double _x, double _y)
    {
        x = _x; y = _y;
    }
    Point(){}
};

void print (const Point& p)
{
    cout << &p << ' ' << &p.x << ' ' << &p.y << endl ;
}

int main()
{
    Point a(2.3,4.7);
    print(a);
    return 0;
}

//địa chỉ của a.x trùng với địa chỉ của biến do được khai báo trước
//địa chỉ của y cách x một khoảng tùy thuộc theo kiểu dữ liệu ( trường hợp này là 8 do kiểu double)

A5.
#include <iostream>

using namespace std;

struct Array
{
    int n;
    int* arr;

    Array(int _n)
    {
        n = _n;
        arr = new int[n];
        for(int i=0;i<n;i++)
            arr[i]=n-i;
    }
    ~Array()
    {
        delete [] arr;
    }
    void print ()
    {
        cout << n << endl ;
        cout << arr << endl ;
        for(int i=0;i<n;i++)
            cout << arr[i] << ' ';
        cout << endl;
    }
};

int main()
{
    Array a(5);
    Array b = a;
    a.print();
    b.print();
    return 0;
}

C1.
#include <iostream>
#include <cstring>

using namespace std;

struct String
{
    int n;
    char* str;
    String(const char* _str)
    {
        n=strlen(_str);
        str = new char[n];
        strncpy(str,_str,n);
    }
    ~String()
    {
        delete [] str;
    }
    void print ()
    {
        cout << str << endl ;
    }
    void append(const char* s)
    {
        int m=n+strlen(s);
        char* tmp=new char[m];
        strncpy(tmp,str,n);
        for(int i=n;i<m;i++)
            tmp[i]=s[i-n];
        delete str;
        str=tmp;
    }
};

int main()
{
    String s("Hi");
    s.append(" there");
    s.print();
    return 0;
} 
