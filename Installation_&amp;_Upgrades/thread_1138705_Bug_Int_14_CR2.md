---
title: "Bug Int 14 CR2"
date: 2009-04-26
forum: Installation &amp; Upgrades
---

### Post by frevh on 2009-04-26
Upgraded 9.04 can't boot

the upgrade went very easely online like i did with previous 2 versions without big problems
but this time ;
Bug Int 14 CR2 ffffb0f0
Edi 0000000...
Eby 000000046
errr 000000...
Stack c011a26e  0000046...

it happens straith after lilo loading Linux
can work with linux old = 8.10

foud some explanation : it seems to be a regression ... I really don't understand this and what can I do ?

thanks

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/312554/+viewstatus](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/312554/+viewstatus)
[https://lists.ubuntu.com/archives/ubuntu-users/2007-June/115671.html](https://lists.ubuntu.com/archives/ubuntu-users/2007-June/115671.html)

---

### Post by tgretton on 2009-04-27
I am using GRUB as my bootloader.

As an interim fix, I resolved the issue by changing

[INDENT]default 0[/INDENT]

to
[INDENT]default [COLOR="Red"]2[/COLOR][/INDENT]

in /boot/grub/menu.lst

This makes 2.26.27-11-generic (the third one in the grub list) my default kernel.  Now, I can either wait for an updated kernel or I can learn how to fix the kernel.

I am not familiar enough with LILO to know what the equivalent fix is...



Tom

---

### Post by apparle on 2009-04-27
I get this error when I put in the jaunty live CD...............should I install jaunty
from alternate CD or continue with 8.10 which is working fine

---

### Post by tgretton on 2009-04-27
It's really your choice.  Do you want the new features/updates/security enhancements/etc. that come with 9.04 or are you happy with 8.10 ?

I had the same problem with the live cd so I did my upgrade from the internet using update-manager.

After completing the upgrade, I booted into Linux using the 2.6.27 kernel and edited /boot/grub/menu.lst.


Tom

---

### Post by apparle on 2009-04-28
But if I do a fresh install I wouldn't have an old kernel so I wouldn't be able to boot at all..........neither will I be able to compile a patched kernel as in the above post..so what should I do??
I do want to install jaunty and try new features.........
Can't I just select an older kernel during alternate installation

---

