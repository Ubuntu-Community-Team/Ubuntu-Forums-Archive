---
title: "Problem with Grub"
date: 2008-12-16
forum: Installation &amp; Upgrades
---

### Post by bcr821 on 2008-12-16
Last year for Christmas i decided to build my mom a "TiVo" with linux using Mythbuntu.

Everything was working great but the past few days my mom tells me that the computer is booting to a command line.  I get here and take a look at it and i see the grub command line.

I've been researching and i cannot get the computer to boot.  I've reinstalled grub (so i think) using these threads:

[http://ubuntuforums.org/showthread.php?t=24113](http://ubuntuforums.org/showthread.php?t=24113)
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

Grub is installed fine (i guess) but, due to my lack of knowledge of grub, i cannot get it to boot anything.  Anytime i try i get error 18 (i guess I'm just pointing it to the wrong place).  I can boot using the liveCD and i can mount the HD so i know that the drive isn't bad i just cannot get the machine to boot.

The only drives i have in the machine is my CD drive and my IDE HDD.  From what i could tell the menu.lst in /boot/grub looks fine (from inside of the liveCD)  I even tried replicating the commands that were generated in menu.lst to try to boot the machine (the commands that worked fine before) but i still am not having any luck.  

Normally I'd just rebuild the box but i put a lot of time and effort into tweaking the box to work exactly how she wants and it will be VERY time consuming to rebuild the box.  Time i don't have right now, plus she's REALLY missing her tivo.  It seems to be something pretty simple but grub wont even bring up the list of boot options, it just goes straight to "grub >"

I'm really at a loss as to what to do and any help would be greatly appreciated.  Thanks in advance.

---

### Post by logos34 on 2008-12-16
i'd check the hdd settings in the bios.  More on error 18 [here]("http://users.bigpond.net.au/hermanzone/p15.htm#18")

---

### Post by bcr821 on 2008-12-16
> **logos34 said:**
> i'd check the hdd settings in the bios.  More on error 18 [here]("http://users.bigpond.net.au/hermanzone/p15.htm#18")

I will, however that drive worked fine for the past year.  Why would it only just now throw an error 18?

Plus once i boot up ubuntu sees the whole drive and i can read all the data off the disk

---

### Post by the8thstar on 2008-12-16
The HDD could broken, scratched or simply put, too full.

---

### Post by logos34 on 2008-12-16
> **bcr821 said:**
> I will, however that drive worked fine for the past year.  Why would it only just now throw an error 18?

Plus once i boot up ubuntu sees the whole drive and i can read all the data off the disk

just throwing out ideas for stuff to try...I know one thing, it can't be a cylinder limit or anything like that.

---

### Post by mrbiggbrain on 2008-12-16
error 18 can be caused by updateing some versions of ubuntu/kubuntu. if updates are being performed automaticly then its possible that an error occoured due to one of those updates.

---

### Post by bcr821 on 2009-01-02
True, however like i said if i boot off of a liveCD i can read all the files no problem.  The drive was not close to full.  Like 180gb/250gb or something like that

---

### Post by bcr821 on 2009-01-02
How can i tell if that is what happened?  I did change it recently to apply updates automatically considering there were like 300+ updates waiting to be installed

---

