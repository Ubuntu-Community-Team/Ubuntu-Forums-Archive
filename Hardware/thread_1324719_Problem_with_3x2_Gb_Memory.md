---
title: "Problem with 3x2 Gb Memory"
date: 2009-11-12
forum: Hardware
---

### Post by wanna_try on 2009-11-12
Hi.
I've just installed 9.10 64bit kubuntu but problem with memory still happened. System monitor show me only 3.1 Gb dynamic memory is installed, although I installed 3 modules 2 Gb of each. How to fix a problem? I want my system to see all memory. 
Hardware: CPU Intel i5, Memory Kingston Hyperx 2000Mhz.

I've installed OS with PXE boot if it matter.
thanx for responding

---

### Post by wanna_try on 2009-11-12
anna@desktop:~$ uname -a
Linux desktop 2.6.31-14-generic #48-Ubuntu SMP Fri Oct 16 14:05:01 UTC 2009 x86_64 GNU/Linux

anna@desktop:~$ lsb_release -a
No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 9.10
Release:        9.10
Codename:       karmic

---

### Post by wanna_try on 2009-11-12
here 's screenshot of sysmonitor
thanx

---

### Post by hal10000 on 2009-11-12
Look into your BIOS and see what amount of RAM it recognizes.

---

### Post by wanna_try on 2009-11-13
in bios evrything is looking ok, it show me all 6 Gb

---

### Post by wanna_try on 2009-11-13
I wondering why this problem is not solved in FAQ, there's so many Q about this theme in internets..

---

### Post by hal10000 on 2009-11-13
Maybe you can solve your problem if you edit the kernel line in your grub configuration file. How to do thid, depends on zhe version of grub you are using.

If you are using jaunty (ubuntu 9.04) or an earlier version, which use the old grub, you have to edit your **/boot/grub/menu.lst** file as root. find the line which looks similar to this one:
```

kernel          /boot/vmlinuz-2.6.28-16-generic root=UUID=1a8cdf2e-e6f9-4020-a751-30f83844bc82 ro quiet splash

```
and edit it to look like this:
```
kernel          /boot/vmlinuz-2.6.28-16-generic root=UUID=1a8cdf2e-e6f9-4020-a751-30f83844bc82 ro quiet splash mem=6144M
```


If you are using karmic (ubuntu 9.10), which by default uses grub 2, i guess you have to edit the file /etc/default/grub as root. Find the line similar to this one:
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
```
and dit it to look like this:
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash mem=6144"
```
But i have to confess that in case of grub2 i'm not absolutely sure, because i have less experience with the new grub version.

You have to reboot after you saved your changes.

Tell me wether that solved your problem. YOu can test it easily by typing the command [COLOR="Red"]free[/COLOR] in a terminal window.

---

### Post by wanna_try on 2009-11-14
I solved this problem - set remap memory switcher in BIOS settings.
This helped.
Thanx

---

