---
title: "pointer freezes"
date: 2010-10-26
forum: Hardware
---

### Post by azertyh on 2010-10-26
hello,
 
i have an issue with my dell vostro 1015 and xubuntu 10.10. after 5 to 10 minutes, the pointer doesn't work during 3 to 5 seconds, works, doesn't work again and so on. and finally the computer becomes slow. a top in a terminal show that Xorg occupies all the CPU.
 
in syslog, i see these messages :
```
[ 4964.557857] psmouse.c: GlidePoint at isa0060/serio1/input0 lost synchronization, throwing 1 bytes away.
[ 4970.803857] psmouse.c: resync failed, issuing reconnect request

```
 
after research, i found some threads about it :
 
- i have already posted here but no response [http://newyork.ubuntuforums.org/showthread.php?t=1597952](http://newyork.ubuntuforums.org/showthread.php?t=1597952)
 
- the bug is already in launchpad [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/641091](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/641091), but the 
```
sudo modprobe -r psmouse
sudo modprobe psmouse
```
don't work for me.
 
- this thread [http://ubuntuforums.org/showthread.php?t=860332](http://ubuntuforums.org/showthread.php?t=860332) advices to modify the file /etc/modprobe.d/options.conf, but there is no such file in 10.10.
 
i have only this issue with xubuntu because i have installed another distro and i don't have this issue.
 
helps are very thankful.
 
edit : found this too [https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/41301](https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/41301)

---

### Post by azertyh on 2010-10-27
**B**ring
**U**p
**M**y
**P**ost

---

### Post by azertyh on 2010-11-04
hello,

tuesday, i updated xubuntu with the new kernel : 2.6.35-22.

i also modify my grub by changing
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
```to
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash noapic nolapic"
```since yesterday, xubuntu has never frozen. i don't know what has solved my problem : the new kernel or the change in grub.

---

### Post by garyvdm on 2010-11-10
I had the same problem with a friends Vostro 1015, as well as a problem with jerkey video playback. Kernal upgrade did not help. Changing the grub options fixed it. :-)

---

### Post by d_v0id on 2011-01-28
Grub options also worked for me, thanks :KS:KS:KS:KS

---

