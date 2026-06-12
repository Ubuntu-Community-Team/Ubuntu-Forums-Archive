---
title: "GTNetS installation problems"
date: 2009-06-25
forum: Installation &amp; Upgrades
---

### Post by tendy on 2009-06-25
Hello, 

I am using ubuntu jaunty, and trying to install GTNetS, and here is the installation manual:

> [COLOR=#000099]_[SIZE=3]Installation Steps[/SIZE]_[/COLOR]
         1. [U]Create Dependency List
        [/U]   
            In the _GTNetS_ (main folder)
            $ make depend
        
        **Note: &#8220;make depend&#8221; may result in an error in the EXAMPLES directory when using the sun studio compilers. This can be safely ignored**
        [U]2. [U]Create libraries with debugging symbols
        [/U]    
            $ make debug
        
        3. [U]Create libraries with optimal code
        [/U]    
            $ make opt
        
         **Note: make sure you have done make depend atleast once after checking out the sources**[/U][U]

First step is a success, but when I do the make debug part, here is the message:

[/U]> [U]root@ubuntu:/home/tendy/Desktop/GTNetS-Oct-10-08# make debug
make -C SRC debug
make[1]: Entering directory `/home/tendy/Desktop/GTNetS-Oct-10-08/SRC'
Compiling debug aiff
g++ -g -fPIC -DLinux -Wall -DHAVE_QT -I/usr/include/qt3  -I/home/tendy/Desktop/GTNetS-Oct-10-08/SRC -o /home/tendy/Desktop/GTNetS-Oct-10-08/OBJDBG/aiff.o -c aiff.cc
aiff.cc: In static member function &#8216;static double AIFF::ConvertFromExtended(char*)&#8217;:
aiff.cc:482: error: &#8216;memcpy&#8217; was not declared in this scope
aiff.cc: In static member function &#8216;static void AIFF::ConvertToExtended(double, char*)&#8217;:
aiff.cc:526: error: &#8216;memcpy&#8217; was not declared in this scope
aiff.cc:528: error: &#8216;memset&#8217; was not declared in this scope
make[1]: *** [/home/tendy/Desktop/GTNetS-Oct-10-08/OBJDBG/aiff.o] Error 1
make[1]: Leaving directory `/home/tendy/Desktop/GTNetS-Oct-10-08/SRC'
make: *** [SRC] Error 2
[/U]When I do the make opt part, here is the error message:

> make -C SRC opt
make[1]: Entering directory `/home/tendy/Desktop/GTNetS-Oct-10-08/SRC'
Compiling opt aiff
g++ -O2 -fPIC -DLinux -Wall -DHAVE_QT -I/usr/include/qt3  -I/home/tendy/Desktop/GTNetS-Oct-10-08/SRC -o /home/tendy/Desktop/GTNetS-Oct-10-08/OBJOPT/aiff.o -c aiff.cc
aiff.cc: In static member function &#8216;static double AIFF::ConvertFromExtended(char*)&#8217;:
aiff.cc:482: error: &#8216;memcpy&#8217; was not declared in this scope
aiff.cc: In static member function &#8216;static void AIFF::ConvertToExtended(double, char*)&#8217;:
aiff.cc:526: error: &#8216;memcpy&#8217; was not declared in this scope
aiff.cc:528: error: &#8216;memset&#8217; was not declared in this scope
make[1]: *** [/home/tendy/Desktop/GTNetS-Oct-10-08/OBJOPT/aiff.o] Error 1
make[1]: Leaving directory `/home/tendy/Desktop/GTNetS-Oct-10-08/SRC'
make: *** [SRC] Error 2:confused::confused:

[B]Can someone help me?? Thanks a lot.. :D
[/B]

---

### Post by mnisar@gmail.com on 2009-07-09
Tendy,

Were you able to solve the problem? I am having same error messages and I was wondering maybe you have a solution by now?

Thanks

Muddy

---

### Post by mnisar@gmail.com on 2009-07-17
You have to add, #include <cstring> in aiff.cc and many other files that will give you similar errors. You might need to include cstdlib header file as well in certain files. After including header files in all the related files, you should be able to run "make debug". However, if you still get an error try "make opt" instead. You should be able to run the simulator.

---

### Post by wjqnudt on 2009-09-06
thank you very much for your help, I solve the problem

---

### Post by abdulkadiradekunle on 2011-04-26
> **wjqnudt said:**
> thank you very much for your help, I solve the problem

Hi, I've the same problem installing it. could you pls help me with the solution.

The make depend command worked, but make debug had error
node-impl.h:362: note: 	virtual NodeAnimation* NodeImpl::GetNodeAnimation() const
make[1]: *** [/home/ahmed/GTNetS-Oct-10-08/OBJDBG/node.o] Error 1
make[1]: Leaving directory `/home/ahmed/GTNetS-Oct-10-08/SRC'
make: *** [SRC] Error 2
ahmed@ahmed-Satellite-C650:~/GTNetS-Oct-10-08$ 


Thanks, as I hope for your support

---

