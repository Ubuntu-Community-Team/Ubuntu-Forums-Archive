---
title: "[Errno 5 ] Input/Output error trying to install"
date: 2009-10-19
forum: Installation &amp; Upgrades
---

### Post by searchfgold6789 on 2009-10-19
At...about...35 percent...at the installation of 9.04 it says Errno 5 then reccomends i clean disk and do some other stuff. This is my second CD, the other cd I made had the same error. Halp! btw I have two Hard disks, one 30GB, another 120GB. The latter has Windows Home, which is not booting, but I don't mind because once I install GRUB everything will be fine. (shhh!) And the 30GB one is the one I'm trying to get Ubuntu on.  :( :( :( :( :KS
 - Richie

---

### Post by stlsaint on 2009-10-19
disconnect the 120hdd or whichever one has windows on it...then re-download the ubuntu 9.04 jaunty iso again and make sure to check the [md5sum]("https://help.ubuntu.com/community/HowToMD5SUM") of the iso prior to downloading. Then burn iso at slowest speed possible. (4x)
then try to install on 30gb. if fails you may have bad hdd!

---

### Post by searchfgold6789 on 2009-10-19
I _*did*_ check the md5sum though! and I just disconnect the windows one, install Ubuntu on the 30GB, reconnect the Windows one, and GRUB will detect Windows?

---

### Post by stlsaint on 2009-10-19
> **searchfgold6789 said:**
> I _*did*_ check the md5sum though! and I just disconnect the windows one, install Ubuntu on the 30GB, reconnect the Windows one, and GRUB will detect Windows?

you will prolly have to add a stanza to menu.lst

---

### Post by searchfgold6789 on 2009-10-19
hrm? :confused:

---

### Post by searchfgold6789 on 2009-10-19
:( Now I am gong to try...yet...*another*...cd.
bai

---

### Post by stlsaint on 2009-10-20
sorry i didnt explain adding a stanza. please see signature for grub help/resource and reference.

---

### Post by searchfgold6789 on 2009-10-21
I'm sorry, I don't get this at all. Back to windows, I guess. :(

---

