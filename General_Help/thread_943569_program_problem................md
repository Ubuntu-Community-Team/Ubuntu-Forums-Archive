---
title: "program problem..............."
date: 2008-10-10
forum: General Help
---

### Post by abhilashm86 on 2008-10-10
cout,cin,endl are not executing when i compile following code........#include<iostream>
int main()
{
 int a[10],i,search;
 cout<<"enter size of array"<<endl;
 int n;
 cin>>n;
 cout<<"enter elements in ascending order"<<endl;
 for(i=0;i<n;i++)
 cin>>a[i];
 int key;
 cout<<"enter key element to be searched"<<endl;
 cin>>key;
 int low=0,high=n-1;
 int bin=search(a,low,high,key);
 if(bin==1)
 cout<<"search sucessfull"<<endl;
 else
 cout<<"unsuccessfull search"<<endl;
}
int search(int a[],int low,int high,int key)
{
 while(low<high)
 {
   int mid=(low+high)/2;
   if(key==a[mid])
   return 1;
    
   else if(key<a[mid])
return search(a,low,high-1,key);
 else
return search(a,low+1,high,key);
}
}


error its giving is..............
abhilash@abhilash-desktop:/bin$ sudo gcc binary.cpp
binary.cpp: In function ‘int main()’:
binary.cpp:5: error: ‘cout’ was not declared in this scope
binary.cpp:5: error: ‘endl’ was not declared in this scope
binary.cpp:7: error: ‘cin’ was not declared in this scope
binary.cpp:15: error: ‘search’ cannot be used as a function


please help to execute the program

---

### Post by rishabh on 2008-10-10
Here's the corrected code:
```

#include<iostream>
**using namespace std;**
int main()
{
int a[10],i,search;
cout<<"enter size of array"<<endl;
int n;
cin>>n;
cout<<"enter elements in ascending order"<<endl;
for(i=0;i<n;i++)
cin>>a[i];
int key;
cout<<"enter key element to be searched"<<endl;
cin>>key;
int low=0,high=n-1;
int bin=search(a,low,high,key);
if(bin==1)
cout<<"search sucessfull"<<endl;
else
cout<<"unsuccessfull search"<<endl;
}
int search(int a[],int low,int high,int key)
{
while(low<high)
{
int mid=(low+high)/2;
if(key==a[mid])
return 1;

else if(key<a[mid])
return search(a,low,high-1,key);
else
return search(a,low+1,high,key);
}
}

```

---

