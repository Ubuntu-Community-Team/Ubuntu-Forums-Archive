---
title: "Problem with boot"
date: 2009-08-03
forum: Installation &amp; Upgrades
---

### Post by hudic20 on 2009-08-03
Hello.

I have one problem. I install Ubuntu 9.04 with Wubi in Win 7 on my PC and work normal. But problem is with install on my laptop (HP Compaq 6820s - graphics card: Ati Mobility Radeon X1350. I dont have any login screen just this: 

```
Booting &#711; Ubuntu 9.04, kernel 2.6.28-11-generic&#711;

 Filesystem type is ntfs, partition type 0x07
The current working directory(i.e., the relative path) is /ubuntu/disks
    [Linux-bzImage, setup=0x3000, size=0x353cd0]
    [Linux-initrd @ 0x7f82c000, 0x773b98 bytes]
Loading, please wait...

Ubuntu 9.04 ubuntu tty1

ubuntu login: _ 
```

and error when type something.

```
E: dpkg was interrupted, you must manually run &#711;sudo dpkg --configure -a&#711; to corect the problem.
```

Whats the problem. :confused: Please help me and sorry if my English is not perfect. :oops:

Thank you for help.

---

### Post by realzippy on 2009-08-03
You have to login...type username,password....then,try,as suggested:

sudo dpkg --configure -a



What happens?

---

### Post by hudic20 on 2009-08-03
Nothing. Just ```
myname@ubuntu:~$
``` and this is it. :(

---

### Post by realzippy on 2009-08-03
There is a big problem:
 
[http://ubuntuforums.org/showthread.php?t=1133931](http://ubuntuforums.org/showthread.php?t=1133931)

Solution:

Do not use Ubuntu 9.04,if you want to use the ATI fglrx driver.
Install Ubuntu 8.10 Intrepid.

Do not use the ATI fglrx driver,if you want Ubuntu 9.04.Use the free driver:


sudo apt-get remove --purge xorg-driver-fglrx


sudo apt-get install --reinstall libgl1-mesa-glx libgl1-mesa-dri

sudo reboot now


Hint:
I would go back to 8.10 !!

---

### Post by hudic20 on 2009-08-03
Ok. :-?

Tnx for answer and help. :wink:

---

