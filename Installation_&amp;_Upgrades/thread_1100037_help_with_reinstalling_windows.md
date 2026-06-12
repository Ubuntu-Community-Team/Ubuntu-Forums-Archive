---
title: "help with reinstalling windows"
date: 2009-03-18
forum: Installation &amp; Upgrades
---

### Post by UserNamehere on 2009-03-18
Hi.  I want to go back to windows after a full ubuntu 8.10 install.  

Can someone help me with this?  Ive searched for answers but didnt
come up with anything.

---

### Post by UserNamehere on 2009-03-18
I do have the recovery cds for my pc.

---

### Post by upchucky on 2009-03-18
with great sadness i provide the info.

put in win cd and install. have it format the entire partition you want windows on.

if you had a dual boot setup then you will need to use the windows cd to fixmbr

if you want a couple of partitions to be able to save your files when windows self destructs you should use the ubuntu cd to make the partitions for windows first.

---

### Post by zvacet on 2009-03-18
Download [Gparted live CD.]("http://gparted.sourceforge.net/")If you want to have just windows on your comp then delete all partitions with Gparted and then install Windows.If you want to dual boot then shrink Ubuntu partition and on unallovated space install Windows.After that [reinstall grub.]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows")

---

