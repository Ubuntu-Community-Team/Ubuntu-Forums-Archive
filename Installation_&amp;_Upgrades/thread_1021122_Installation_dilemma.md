---
title: "Installation dilemma"
date: 2008-12-25
forum: Installation &amp; Upgrades
---

### Post by fababhi on 2008-12-25
I have a dual boot PC with Windows XP and Ubuntu 8.10. circumstances are such that i have 2 format Windows XP i.e the partition its installed on. but i am afraid am gonna lose Ubuntu because da format will delete the wubildr and wubildr.mbr files. Please suggest a solution to save Ubuntu...will temporary displacement of wubildr and wubildr.mbr files on another partition help ? what i mean is, placing them back on the partition where XP will be installed after the format ? because after the format i am gonna lose the option of choosing the OS .. what can be done ?

 please help ...

---

### Post by namdung on 2008-12-25
I reckon u have 2 partitions C and D Drive. You have installed Ubuntu using wubi in D drive. Now u want to format C drive.

Firstly if u really like Ubuntu than do not use wubi anymore. WUBI is more of *try before u buy* and lacks performance & certain features. 

If u still want to use wubi, u should be able to get restore Ubuntu in D after format but do reconsider moving onto full blown Ubuntu installation in one partition.

[http://ubuntuforums.org/showthread.php?t=1020050](http://ubuntuforums.org/showthread.php?t=1020050)

---

### Post by balaknair on 2008-12-25
1) From within Windows, within the C:\Ubuntu folder, look for a file named root.disk. This is the virtual disk image on which your Ubuntu is installed. Copy this file and save it somewhere safe on another partition or drive. 
***** *(Also, if you just downloaded Wubi.exe and not the CD, copy the 699 MB .iso file(that's the Ubuntu CD image) that wubi downloaded.)*

2) Format C:\, install Windows XP or whatever else you need to do.
3) Now again install wubi
***** *if installing via the wubi.exe file and not from the Wubi installer on the CD, copy the .iso file you saved into the same folder as wubi.exe before running wubi.exe*

4) Now that you have new working copy of Wubi, find the new root.disk within the new C:\Ubuntu folder, and replace it with the one you saved earlier.

You should have things back as it was before the Windows reinstall. Just make sure that the versions of Wubi and Ubuntu you use this time are the same as what you had earlier.

---

