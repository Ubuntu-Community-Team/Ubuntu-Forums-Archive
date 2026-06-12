---
title: "absolute value with g++ compiler"
date: 2009-03-10
forum: Installation &amp; Upgrades
---

### Post by Destro09 on 2009-03-10
I was wondering if anyone else is having problems with the absolute value function, abs(), with the latest update of g++ version 4.3.2 and if there is a way to fix it?

I did #include<cmath> with one trial and #include<math.h> with another.  One compile says the function abs() cannot be found and the other says that the abs() function expects data type of float or double.

I'm trying to find the absolute value of an integer by the way.  Plus the file does has a .cpp extension and I made sure I have #include<iostream> and using namespace std;

The reason I'm asking about this g++ version is because my friend has g++ version 4.0.1 and his computer compiles the same code fine.  Any suggestions would be helpful.  Thanks.

---

### Post by Neo_The_User on 2009-03-10
ABS... Archlinux build system? Is this a question about Ubuntu or no?

---

### Post by Simian Man on 2009-03-10
> **Neo_The_User said:**
> ABS... Archlinux build system? Is this a question about Ubuntu or no?

So...did you even read his post?

I'm not sure why the compiler says abs() is defined that way.  I don't really care for how C++ overloads standard library functions, it leads to crap like this.

Anyway you can use the following macro to robustly define absolute value:
```

#define ABS(X) ((X) > 0 ? (X) : (-(X)))

```

---

### Post by Neo_The_User on 2009-03-10
> **Simian Man said:**
> So...did you even read his post?

I'm not sure why the compiler says abs() is defined that way.  I don't really care for how C++ overloads standard library functions, it leads to crap like this.

Anyway you can use the following macro to robustly define absolute value:
```

#define ABS(X) ((X) > 0 ? (X) : (-(X)))

```

yeah i read it

---

### Post by issih on 2009-03-10
One possibility is that at some point (I don't know at what version number) g++ started being particular about using namespaces properly, when it never was before.

try putting ```
using namespace std;
``` at the start of your code and seeing if it will compile like that, or alternatively explicitly state the namespace with std::abs(x) instead of just abs(x).

Hope that helps

---

### Post by Destro09 on 2009-03-10
So far 

#define ABS(X) ((X) > 0 ? (X) : (-(X)))

does work.  However, isn't this just like righting a function to detect numbers less than zero and then multiplying by -1?  I understand how to fix the code by writing the absolute value function, but that isn't exactly what I was looking for.  I do appreciate the help though.

I had using namespace std; in the original program and adding std:: infront of the abs(x); generates the error that 'abs' is not a member of 'std'

Unfortunately, it seems to be a problem with my version of g++ 4.3.2 because the same code works fine with g++ version 4.0.1.

Thanks for the help.



NEO, I understand this is an ubuntu forum.  However, since the g++ and gcc compiler functions are in my Synaptic Package Manager, which is part of ubuntu, I figured that the Installation & UPGRADES portion of the forum might be a good place to look for some help with the problem I am having.  There happen to be a lot of people that read these posts that know more about this than me and sometimes they are willing to help.

---

### Post by Neo_The_User on 2009-03-10
M'kay. true. you have a point.

---

