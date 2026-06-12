---
title: "Replaced graphics card with ATI5770, now X won't start"
date: 2010-06-21
forum: Hardware
---

### Post by leondz on 2010-06-21
Hi,

I recently upgraded from an ATI 4550 to a 5770 on my ubuntu 9.10 dual-boot box (other OS is XP). However, startx no longer works, complaining of "no screen available". I have tried apt-get upgrade then also removing all the fglrx packages and re-installing xorg-drivers-fglrx , but the same error persists. How can I install the correct driver from the command line?

---

### Post by Yellow Pasque on 2010-06-21
Start by removing the old driver, then go to the beginning of the "manually install the driver" section of this guide (it will work on Karmic too): [http://wiki.cchtml.com/index.php/Ubuntu_Lucid_Installation_Guide#Removing_the_Driver](http://wiki.cchtml.com/index.php/Ubuntu_Lucid_Installation_Guide#Removing_the_Driver)

---

