---
title: "not able to install systemc on ubuntu after typing make command"
date: 2009-09-03
forum: Installation &amp; Upgrades
---

### Post by anshul_nit on 2009-09-03
i am using ubuntu ultimate 2.3
it is having gcc and g++ already
but whenver i try to install systemc on it by typing command in terminal 
1)./configure (it works fine)
2)make (it gives me error ike this)
make[3]: *** [sc_utils_ids.o] Error 1
make[3]: Leaving directory `/home/satvik/Desktop/system/src/sysc/utils'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/home/satvik/Desktop/system/src/sysc'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/satvik/Desktop/system/src'
make: *** [all-recursive] Error 1
3)make install(also giving error)

I have installed it many times on the previous version of ubuntu ultimate..bt that time there was no error, but this time i am not able to understand..
plz help me in figuring out what could be the cause??

---

### Post by anshul_nit on 2009-09-03
plz help me out

---

### Post by anshul_nit on 2009-09-21
:(

---

### Post by stlsaint on 2009-09-21
i too run UE 2.3 and i know that build-essential does not come pre-installed...

sudo apt-get install build-essential  
then
sudo apt-get update
and try make again

---

### Post by wurzel529 on 2009-10-17
I had the same problem and fixed it in the source code. It fixes a missing #include-directive in
src/sysc/utils/sc_utils_ids.cpp and excludes the examples directory from building because it
caused problems using 'make install'.

You can download my patch from [http://www.embedded-system-design.de/download/systemc-2.2.0-ubuntu9.04.patch](http://www.embedded-system-design.de/download/systemc-2.2.0-ubuntu9.04.patch) ...

Apply it by typing:

  cd systemc-2.2.0
  patch -p1 < ../systemc-2.2.0-ubuntu9.04.patch

... as well as (due to missing automake-1.6):

  aclocal
  automake
  autoconf

Now, you can configure and compile SystemC by

  ./configure
  make
  make install

Best regards!

---

### Post by parinaz.sayyah on 2010-05-21
Hi,

I had same errors! I fixed it by going through installation steps as below:

1.  tar xvf systemc-2.2.0.tar
2.  cd systemc-2.2.0
3.  mkdir objdir
4.  cd objdir
5.  which g++ (To check if g++ is available in yr path)
6.  ../configure
[COLOR="Red"]7.[/COLOR]  [COLOR="Red"]mkdir home/usr/sysc
8.  ../configure --prefix=/home/usr/sysc[/COLOR]
9.  make
10. make debug
11. make install

On ubuntu is important to create a directory as said in step 7, you can call it simply  "sysc" or any other name, but it is important that you install and do configure in the new created file. 

If you still get errors, try to add these includes: 

#include "string.h"
#include "cstdlib"

to systemc-2.2.0/src/sysc/utils/sc_utils_ids.cpp

and go through above steps again!

---

### Post by maanrl on 2010-11-07
The solution provided by _[wurzel529]("http://ubuntuforums.org/member.php?u=932335")_ worked for me, thanks.

---

### Post by ahaxin on 2010-11-08
To fix this problem, add the following includes at the top of file
../src/sysc/utils/sc_utils_ids.cpp:
#include<cstdlib>
#include<cstring>

---

