---
title: "C++ help"
date: 2008-09-25
forum: General Help
---

### Post by Cyberbanana1 on 2008-09-25
Okay, tonight, our homework is to make a c++ program that takes 10 inputed numbers and averages them, using the for function thing. The code i wrote so far, although i have no idea if it works, is 

#include <iostream> 
using namespace std;
int main(void)

int i, temp, sum
for(i=1; i<11; i=i+1) {
cout << "Enter number" '\n';
cin >> temp;
sum=sum+temp;
}
cout << sum/10i;

when i try to compile this, i get errors:

average.cpp:5: error: expected initializer before ‘int’
average.cpp:6: error: expected constructor, destructor, or type conversion before ‘<’ token
average.cpp:6: error: expected constructor, destructor, or type conversion before ‘=’ token
average.cpp:11: error: expected constructor, destructor, or type conversion before ‘<<’ token


help would be much appreciated. I'm still pretty pretty bad at C++. Thanks. Or, other ideas to help me accomplish this while using a "for" loop thing works too.

---

### Post by lisati on 2008-09-25
I'm no C++ guru but suspect there are one or two missing semicolons....

---

### Post by d4ni on 2008-09-25
Here you go

```
#include <iostream>
using namespace std;

int main(void){

int temp=0, sum=0;
for(int i=1; i<11; i++) {
cout << "Enter number\n";
cin >> temp;
sum=sum+temp;
}
cout << sum/10;
}

```

---

