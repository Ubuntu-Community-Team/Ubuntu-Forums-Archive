---
title: "Trackpad stops working"
date: 2018-09-16
forum: Hardware
---

### Post by wmdiem on 2018-09-16
Hi all. I'm currently running ubuntu 18.04 off a USB in a live session, on a lenovo Flex 6-11IGM (81A7).

> ubuntu@ubuntu:~$ uname -a
Linux ubuntu 4.15.0-29-generic #31-Ubuntu SMP Tue Jul 17 15:39:52 UTC 2018 x86_64 x86_64 x86_64 GNU/Linux


The trackpad randomly stops working. It could be after a second or after tens of minutes. I can say that it does seem to be connected to use of the laptop; I left it up overnight and the trackpad was still working this morning. 

When it stops working the computer remains responsive and  the keyboard continues to work. (Not the touchscreen, but the touchscreen never works and is another issue). 

Before it stops working my dmesg log gets filled with lines like this, every time I touch the trackpad: 

> [ 6079.727465] i2c_hid i2c-ELAN0630:00: i2c_hid_get_input: incomplete report (14/65535)
[ 6079.733692] i2c_hid i2c-ELAN0630:00: i2c_hid_get_input: incomplete report (14/65535)


(I understand that this spamming the log is a known bug in the i2c_hid module.)

Once it stops working, those messages stop. 

I can get it working again by removing and reinserting the i2c_hid module. 

I'm not sure how to go about troubleshooting this further. I know that I could just install ubuntu, do an upgrade, and cross my fingers, but I'm reluctant to do an install without being confident that there is a fix for this issue. 

Any help would be much appreciated. 

Thanks in advance.

---

### Post by wmdiem on 2018-09-16
Well, it turns out this is--so far as I can tell--fully supported in Linux Mint 19 (including the touchscreen! and the log spamming bug is gone!). 

> Linux mint 4.15.0-20-generic #21-Ubuntu SMP Tue Apr 24 06:16:15 UTC 2018 x86_64 x86_64 x86_64 GNU/Linux

> mint@mint:~$ lsb_release -a
No LSB modules are available.
Distributor ID:	LinuxMint
Description:	Linux Mint 19 Tara
Release:	19
Codename:	tara


---

### Post by wmdiem on 2018-09-20
After a kernel upgrade in Mint, it stopped working. 

I've been able to trace it back. The trackpad bugs were introduced in 4.15.0-24. 4.15.0-23 is not affected by either of them.

---

