---
title: "Attempting to install Ubuntu on laptop keeps looking for lan"
date: 2009-03-12
forum: Installation &amp; Upgrades
---

### Post by suri.mahendra on 2009-03-12
I am trying to install Ubuntu 8.10 (32 bit) on a presario zv5000.  I was able to change the boot sequence, however I am unable to proceed after that.

I get a message:  For Realtek.... PCI fast ethernet contoller
       PXE-E61  Media test failure, check cable
       PXE-M0F  exiting pxe ROM

Do I have a bad burn and the laptop is looking for an internet connection.
If I have a bad burn how do I verify this?  How do I verify a good burn?

Thanx

---

### Post by thesavager on 2009-03-12
Hi,

Are you sure you changed boot sequence to "cd" ?
Cause it seems,it wants to boot from network.

If you have a bad burn , it just stops.
You can check if cd is good , when you cd boot,there is an option for it. :)

cheers..

---

### Post by thesavager on 2009-03-12
I found something for you on the internet, its in dutch, so i explain to you.

[http://gathering.tweakers.net/forum/list_messages/1206390](http://gathering.tweakers.net/forum/list_messages/1206390)

The guy found the problem, one of his memory-banks was defect.
In bios he turned on "fullboot" , and tested each memory-bank seperate, to  find out wich one it was.

After that , he only had to repair the MBR.

hope this some help for you.. cheers

---

### Post by suri.mahendra on 2009-03-13
thanks to thesavager.  reviewed all the bonehead things and I didn't burn the iso at or below 4x.

Once I burned the iso at 4x everything went to the cd/dvd drive and now kubuntu 8.10 is installed.  Just having trouble getting mp3 play.

looking thru forums to resolve.....done it before.

---

### Post by abn91c on 2009-03-13
> **suri.mahendra said:**
> thanks to thesavager.  reviewed all the bonehead things and I didn't burn the iso at or below 4x.

Once I burned the iso at 4x everything went to the cd/dvd drive and now kubuntu 8.10 is installed.  Just having trouble getting mp3 play.

looking thru forums to resolve.....done it before.
you neeed this file **libxine1-ffmpeg**, its in the ubuntu-restricted extras package

---

