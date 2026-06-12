---
title: "Installing QT"
date: 2009-06-14
forum: Installation &amp; Upgrades
---

### Post by bargi on 2009-06-14
Hi,

I want to install QT in my system.

I have binary and I am trying to install it using following command:

> 
bash: ./qt-sdk-linux-x86_64-opensource-2009.02.bin: cannot execute binary file



I have changed it permission by using command:

> 
chmod u+x qt-sdk-linux-x86_64-opensource-2009.02.bin


but it is giving following error:
> 
bash: ./qt-sdk-linux-x86_64-opensource-2009.02.bin: cannot execute binary file



Have any idea to install it  ?

Thanks

---

### Post by zaleksf on 2009-06-14
Hi,

I had luck using the following two commands on my 32-bit Ubuntu 9.04 system:

chmod u+x qt-sdk-linux-x86-opensource-2009.02.bin
./qt-sdk-linux-x86-opensource-2009.02.bin

Then a nice installation GUI started. Good luck!

---

