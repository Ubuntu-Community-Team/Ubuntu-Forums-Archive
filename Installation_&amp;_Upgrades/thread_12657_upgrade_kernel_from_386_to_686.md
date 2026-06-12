---
title: "upgrade kernel from 386 to 686"
date: 2005-01-26
forum: Installation &amp; Upgrades
---

### Post by sharkzf6 on 2005-01-26
I'm a Linux newb. I tried Debian but had to use Woody - Sarge wouldn't install on my system with Debian packages. I stumbled across ubuntu and it installed flawlessly. I was very impressed! Anyway, I noticed after doing uname -r my kernel is 2.6.8.1-3-386 or 2.6.8.1-13 according to synaptic. I'd like to upgrade to 2.6-686 since I have a P3 in this system. According to synaptic, the kernel upgrade is the same for -386 and -686, it's listed as 2.6.8.1-14. How do upgrade the kernel and make sure it's using the -686 version? Or am I missing something altogether? Thanks.

---

### Post by sharkzf6 on 2005-01-26
Oh, one other thing. If I decide to install ubuntu on my P4 Prescott system – very likely – will the installer install the -686 SMP kernel or will I have to update that as well? In other words, does the install disk have the -686 SMP kernel on it?

My main concern is that Linux does not support my audigy (24 bit) sound card on my P4 rig. It works great with the SB live! in this box.  :D

---

### Post by rudi on 2005-01-26
this post in the FAQ forum [http://www.ubuntuforums.org/showthread.php?t=3713](http://www.ubuntuforums.org/showthread.php?t=3713) shows how to upgrade your kernel. Look at #9

---

### Post by ctt1wbw on 2005-01-26
That's a good question.  I'm using a relatively newer Inspiron 8600 with a Pentium 4 mobile chip.  My Ubuntu install shows 2.6.8.1-3-386.  What advantages would I get from upgrading.  I've heard that the kernel upgrade disables wireless...

---

### Post by sharkzf6 on 2005-01-26
[QUOTE=rudi]this post in the FAQ forum [http://www.ubuntuforums.org/showthread.php?t=3713](http://www.ubuntuforums.org/showthread.php?t=3713) shows how to upgrade your kernel. Look at #9[/QUOTE]Thanks!  :)

---

### Post by sharkzf6 on 2005-01-26
[QUOTE=ctt1wbw]That's a good question.  I'm using a relatively newer Inspiron 8600 with a Pentium 4 mobile chip.  My Ubuntu install shows 2.6.8.1-3-386.  What advantages would I get from upgrading.  I've heard that the kernel upgrade disables wireless...[/QUOTE]I think the -686 kernel will give the correct drivers for the P2 and higher chipset instead of using Linux generic ones. Also, make sure you get the 2.6.8.1-16-1, not the -14.1. The reason for this is as follows according to synaptic:> It also contains scripts that try to ensure that the system is not left in a unbootable state after an update.
cheers! :D

---

### Post by andy_sp1ke on 2005-01-26
Does P2 upwards include a 2.6 celeron chip (i am pretty sure it does but want to check as have my machine nicely setup at the moment!)

Andy

---

### Post by Recked on 2005-01-26
Hi,

Is there a kernel for dual Athlon processors or do we use the i686 SMP version?

thanks

---

### Post by rudi on 2005-01-26
use the following command for a list of available kernels via apt-get ```
apt-cache search linux | grep kernel
```

---

### Post by Recked on 2005-01-26
Thanks. I assume since I cannot seem to get to root that I need to sudo first?

---

### Post by sharkzf6 on 2005-01-26
[QUOTE=rudi]do a  ```
apt-cache search linux | grep kernel
```, then you'll get a list of available kernels via apt-get[/QUOTE]

Or, if you want something easier, try synaptic. Just launch it from "Computer" - "System Configuration" - "Synaptic Package Manager" and tell it to check your repositories and update them, it's GUI so it's easy.  ;)

---

### Post by Recked on 2005-01-26
Ya I did this the other night, but felt a bit foolish as I had no way to know if the system was actually running the new kernel after I ran it from Synaptic. Is there a command I can run now to check to see if the i686 SMP kernel is on the system. I installed this one as there wasn't one for dual Athlon XP processors which I have.

Appreciate the help thanks

---

### Post by sharkzf6 on 2005-01-26
[QUOTE=Recked]Ya I did this the other night, but felt a bit foolish as I had no way to know if the system was actually running the new kernel after I ran it from Synaptic. Is there a command I can run now to check to see if the i686 SMP kernel is on the system. I installed this one as there wasn't one for dual Athlon XP processors which I have.

Appreciate the help thanks[/QUOTE]

Synaptic tells you what's currently installed but you can just open a terminal and type 'uname -r' and it will tell you.  :-$

---

### Post by ctt1wbw on 2005-01-26
[QUOTE=sharkzf6]I think the -686 kernel will give the correct drivers for the P2 and higher chipset instead of using Linux generic ones. Also, make sure you get the 2.6.8.1-16-1, not the -14.1. The reason for this is as follows according to synaptic:
cheers! :D[/QUOTE]


Um, yeah, that would be, uh bad.   :)

---

### Post by ctt1wbw on 2005-01-26
[QUOTE=Recked]Ya I did this the other night, but felt a bit foolish as I had no way to know if the system was actually running the new kernel after I ran it from Synaptic. Is there a command I can run now to check to see if the i686 SMP kernel is on the system. I installed this one as there wasn't one for dual Athlon XP processors which I have.

Appreciate the help thanks[/QUOTE]


From root, type:

uname -r

---

### Post by ctt1wbw on 2005-01-26
[QUOTE=ctt1wbw]That's a good question.  I'm using a relatively newer Inspiron 8600 with a Pentium 4 mobile chip.  My Ubuntu install shows 2.6.8.1-3-386.  What advantages would I get from upgrading.  I've heard that the kernel upgrade disables wireless...[/QUOTE]

Okay, on a chance I updated the kernel to the i686 version.  Wireless is still going like a champ.

But I noticed that on the grub menu, the other two kernel versions show up as bootable OS's...  is this normal and if not, how do I get rid of the older versions if I don't need them anymore?

Is it:

apt-get uninstall "kernel"

That's right?

---

### Post by rudi on 2005-01-26
That's normal :) ubuntu puts (lets say, leaves) them there in case the new one doesn't work well. You can remove them from you list by editting menu.lst
 ```
sudo gedit /boot/grub/menu.lst
```
 
 It's:
 ```
 apt-get remove foo
```

---

### Post by rh6866 on 2005-01-26
[QUOTE=ctt1wbw]Okay, on a chance I updated the kernel to the i686 version.  Wireless is still going like a champ.

But I noticed that on the grub menu, the other two kernel versions show up as bootable OS's...  is this normal and if not, how do I get rid of the older versions if I don't need them anymore?

Is it:

apt-get uninstall "kernel"

That's right?[/QUOTE]

The older versions are there as a fall back, to boot into in case the new kernel flakes out on you.  

I updated my AthlonXP 2400+ over the weekend, using synaptic, to the latest K7 kernel and after booting into it and working with it a few days, I again used synaptic to remove the 386 kernel, which also automaticaly removed the 386 kernel choice my Grub menu.  

Just to check again I opened synaptic to check to see what it showed as the installed kernel and it was only the K7 one.

---

### Post by ctt1wbw on 2005-01-26
What kind of upgrades or enhancements does the new 686 kernel give?  I haven't really noticed anything yet.

---

### Post by martinlk on 2005-01-27
[QUOTE=ctt1wbw]What kind of upgrades or enhancements does the new 686 kernel give?  I haven't really noticed anything yet.[/QUOTE]

The 686 kernel has been compiled for the instruction set of a 686 processor (Pentium II/III/IV). This should result in better performance compared to using a kernel compiled for the 386 instruction set, which is the lowest common divisor for all x86 processors (meaning that all x86 processors will run this kernel). The end result of using a 686-optimized kernel will probably not be *that* noticable to a typical desktop user, but in general the kernel will operate faster (or more optimized).

---

### Post by ctt1wbw on 2005-01-27
Okay, thanks for that bit.  Learning more and more day by day. :)

---

### Post by sharkzf6 on 2005-01-27
[QUOTE=martinlk]The 686 kernel has been compiled for the instruction set of a 686 processor (Pentium II/III/IV). This should result in better performance compared to using a kernel compiled for the 386 instruction set, which is the lowest common divisor for all x86 processors (meaning that all x86 processors will run this kernel). The end result of using a 686-optimized kernel will probably not be *that* noticable to a typical desktop user, but in general the kernel will operate faster (or more optimized).[/QUOTE]Yeah, I've done it several times since I posted this, both on my P3 and P4 rigs. I noticed a very slight improvement in both cases.  :grin:

---

