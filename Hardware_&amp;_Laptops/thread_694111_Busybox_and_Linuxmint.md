---
title: "Busybox and Linuxmint"
date: 2008-02-11
forum: Hardware &amp; Laptops
---

### Post by narehart on 2008-02-11
Okay, I've searched around a little and I can't seem to find a solution to my problem. This problem has plagued me since Feisty.  I have two hard drives one is IDE one is SATA.  My Linux Mint installation resides on the SATA and my XP installation is on the IDE.  

Back when I was using Feisty the numbers assigned to the partitions would randomly change.  For instance, hda1 would suddenly become hdb1 after a reboot and I'd have to edit my fstab and remount everything anytime that happened.  Eventually, somebody on this forum suggested using UUIDs for each partition and that ended up solving my problems.

When Gutsy was released I did a fresh install with both drives connected.  After the installation was finished I was unable to boot into either XP or Gutsy.  I checked fstab and the partitions were assigned UUIDs. So I unplugged the IDE drive (the one with XP on it) and reinstalled.  After that I was able to boot into either OS by choosing a hard drive from the BIOS boot menu.

That setup was working until I did a little too much experimenting with Gutsy and it seemed kind of messed up (slow boot time, graphical errors...).  So, I decided to try out Linux Mint.  Now, I know Mint is based off of Ubuntu and I was almost sure I'd have the same issue with my hard drives I had before but I thought I'd try to install it with both of them connected anyways.  Of course, it didn't work. 

After that I figured I'd just install Mint again and boot into the hard drives using the BIOS like I had done before.  The install went fine but when I reconnected my IDE drive and booted into Mint it took me to Busybox.  I tried typing exit but it didn't do anything.

So, I'd like to know if anyone has a solution to this problem.  I really like Mint and would prefer to keep it but I need to get into XP for various things.  Any help on this would be greatly appreciated.

---

### Post by narehart on 2008-02-14
Bump

---

### Post by narehart on 2008-02-14
Bump

---

### Post by narehart on 2008-02-14
Bump

---

### Post by NilsHG on 2008-02-18
i had mint installed today and it worked fine until reboot. 

i reinstalled and all i get is busybox

ideas?

---

### Post by narehart on 2008-02-29
I figured this out. You have to change menu.lst and replace "root=dev/sdax" with the UUID of the partition that Linux is installed on.

---

