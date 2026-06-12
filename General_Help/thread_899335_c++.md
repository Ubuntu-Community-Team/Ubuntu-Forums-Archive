---
title: "c++"
date: 2008-08-24
forum: General Help
---

### Post by charanpreethu on 2008-08-24
if i execute c++ prog ........i will get no iostream.h
what shud i install???

---

### Post by bthoward on 2008-08-24
Try using <iostream> (no .h) instead.  If you run your code through gcc it'll tell you there are MANY other options that are better than iostream.h (if editing the code is an option)

---

### Post by sameerds on 2008-08-24
> **charanpreethu said:**
> if i execute c++ prog ........i will get no iostream.h
what shud i install???

It's difficult to say what is going wrong without looking at the code itself. Can you post a program that produces this error on your machine? Make it as short as possible, maybe just a program that prints "hello world".

One thing to point out here is that C++ discourages the use of "iostream.h" ... your include line should say "#include <iostream>" ... without the final ".h"

---

### Post by charanpreethu on 2008-08-24
wat shud be the extension......*.c or *.cpp

---

### Post by charanpreethu on 2008-08-24
#include<iostream>
int main()
{
cout<<"hello";
return 0;
}

program name c++.c

errors im gettin are
c++.c:1:19: error: iostream: No such file or directory
c++.c: In function &#8216;main&#8217;:
c++.c:4: error: &#8216;cout&#8217; undeclared (first use in this function)
c++.c:4: error: (Each undeclared identifier is reported only once
c++.c:4: error: for each function it appears in.)

---

### Post by cmay on 2008-08-24
```

#include<iostream>
using namespace std;
int main()
{
cout<<"hello"<<endl;
return 0;
}
```


this should compile if build-essentials are installed
sudo apt-get build-essential.

hope it helps.

edit
save as hello.cpp
compile g++ ./hello.cpp
run ./hello

---

### Post by charanpreethu on 2008-08-24
its workin..........
can you pls tell  wat is the significance of using namespace std;

---

### Post by cbdonohue on 2008-08-24
This site explains it well:
[http://www.cplusplus.com/doc/tutorial/namespaces.html]("http://www.cplusplus.com/doc/tutorial/namespaces.html")

---

