---
title: "cutecom problem"
date: 2008-07-15
forum: General Help
---

### Post by raedbenz on 2008-07-15
Hi,,
i am using cutecom with /dev/ttyUSB0 (USB serial converter).
i have reinstalled Linux ubuntu8.04, bcoz of some problems i had with my PC.
and know i am trying to use xmodem or ymodem in cutecom to send files and it doesn't work. (previously it was working fine)
any hint?
thanks

---

### Post by ra2008 on 2008-07-18
hi guys, i have sam prob, i tried to send from cutecom using xmodem, ymodem from different PCs running ubuntu i didn't work,. under windows using hyperterminal it worsk,,
any hints??

---

### Post by usman12 on 2008-08-02
i've installed cmake and now i'm trying to install cutecome but it gives the following message

CuteCom uses the CMake build system, at least version 2.4.3 is required.
If there is no package for your distribution, you can
get it from [http://www.cmake.org/HTML/Download.html](http://www.cmake.org/HTML/Download.html)

So instead of running ./configure, you need to run cmake:
$ cmake .


Anyone? help.

---

### Post by raedbenz on 2008-08-02
the "cmake" is used to install cutecom, and in my case i have intsalled properly, and i can use it, but i cant send files from it, but in hyperterminal it works.
thanks

---

### Post by ZEROtech on 2009-12-10
In the readme there is a reference that you need zs tools so by doing ```
sudo apt-get update
```
```
sudo apt-get install lrzsz
```
Or by going into Synaptic and searching for sz tools.
The ymodem that i needed is now functional so i hope that this will help somebody :D

Bye!

---

### Post by arun. on 2011-03-25
It helps. thanks a ton.

---

### Post by celem on 2011-07-07
Except that lrzsz has a bug if you want to use xmodem. It still isn't fixed as of July, 2011

Read:
[https://bugs.launchpad.net/ubuntu/+source/lrzsz/+bug/270638]("https://bugs.launchpad.net/ubuntu/+source/lrzsz/+bug/270638")

and

[http://fossplanet.com/f10/%5Bbug-270638%5D-re-lrzsz-xmodem-doesnt-work-139346/]("http://fossplanet.com/f10/%5Bbug-270638%5D-re-lrzsz-xmodem-doesnt-work-139346/")

I have tried to compile lrzsz so that I can use the patch but have not been successful getting a good compile.

---

