---
title: "Can't compile Xpad drivers!"
date: 2008-10-28
forum: Hardware
---

### Post by Dawey on 2008-10-28
Hi everyone!

I use Ubuntu 8.10 with kernel 2.6.27-7-generic, and I have installed Linux-headers for that kernel. 

I am trying to compile xpad drivers for my Wireless Microsoft Receiver and Wireless controller.

I followed this guide: [https://help.ubuntu.com/community/Xbox360Controller](https://help.ubuntu.com/community/Xbox360Controller) and I downloaded the files and made my own Makefile. When I try to compile it by typing 

[email]david@david-computer:~/.xpad[/email]$ sudo make

I get the following error message:

[SIZE="1"]make modules -C /usr/src/linux-headers-2.6.27-7-generic SUBDIRS=/home/david/.xpad
make[1]: Entering directory `/usr/src/linux-headers-2.6.27-7-generic'
  CC [M]  /home/david/.xpad/xpad.o
/home/david/.xpad/xpad.c: In function ‘xpad_open’:
/home/david/.xpad/xpad.c:382: error: ‘struct input_dev’ has no member named ‘private’
/home/david/.xpad/xpad.c: In function ‘xpad_close’:
/home/david/.xpad/xpad.c:408: error: ‘struct input_dev’ has no member named ‘private’
/home/david/.xpad/xpad.c: In function ‘xpad_probe’:
/home/david/.xpad/xpad.c:496: error: ‘struct input_dev’ has no member named ‘cdev’
/home/david/.xpad/xpad.c:497: error: ‘struct input_dev’ has no member named ‘private’
make[2]: *** [/home/david/.xpad/xpad.o] Error 1
make[1]: *** [_module_/home/david/.xpad] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.27-7-generic'
make: *** [all] Error 2
[/SIZE]

I guess there are something wrong with the xpad driver and newer kernel versions. Does anyone have any solution?

---

### Post by lunarcloud on 2008-10-28
That guide is old, are you sure it didn't work before you tried to do all that?

---

### Post by renato83 on 2008-11-28
Hi all!

I already post the solution to this problem there

[http://www.gs1.ubuntuforums.org/showthread.php?p=6267529&posted=1#post6267529]("http://www.gs1.ubuntuforums.org/showthread.php?p=6267529&posted=1#post6267529")

---

