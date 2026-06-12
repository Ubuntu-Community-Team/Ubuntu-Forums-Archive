---
title: "[SOLVED] Multiple Ubuntu on hard drive"
date: 2008-11-08
forum: General Help
---

### Post by thelugnut on 2008-11-08
I now have dual boot with Ubuntu 8.04 and Windows Xp/SP3. Everything is working fine.

I have an empty partition available, formatted ext3.

I want to install Ubuntu 8.10 into this empty partition.

My question is about GRUB. Right now it only displays Windows XP and Ubuntu 8.04. When I install Ubuntu 8.10 it only displays Windows XP and Ubuntu 8.10.

How do I have GRUB display all three op systems?
:confused:

---

### Post by plucky on 2008-11-08
> When I install Ubuntu 8.10 it only displays Windows XP and Ubuntu 8.10.


Have you already installed it onto your hard drive?


When you install 8.10,it should take over the Grub boot menu and include the 8.04 install in the "other operating system" section of menu.lst.Provided of course you allowed it to during the install.

Boot 8.10 and from a terminal,post the output of these commands```
sudo fdisk -l
cat /boot/grub/menu.lst
```


Good Luck

---

### Post by thelugnut on 2008-11-08
Many thanks for your reply, plucky.

> When you install 8.10,it should take over the Grub boot menu and include the 8.04 install in the "other operating system" section of menu.lst.Provided of course you allowed it to during the install.


And that's exactly what it did.

I must have done something coo-coo the first time. I don't know what I did wrong, but... I redid the install and everything came out just fine.

I appreciate your response.:guitar:

---

