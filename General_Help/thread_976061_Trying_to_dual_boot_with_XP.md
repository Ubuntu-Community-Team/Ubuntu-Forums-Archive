---
title: "Trying to dual boot with XP"
date: 2008-11-08
forum: General Help
---

### Post by matthew937 on 2008-11-08
Hi I just installed Ubuntu 8.10 and I am trying to dual boot with Win XP. Currently, my Ubuntu partition takes up half my drive and the rest is unformatted. When I load the XP install disc it tells me I have no hard drive in the computer. Does Anyone know why this is? I just need a little help getting this sucker running.

---

### Post by Afkpuz on 2008-11-09
You need to install XP first.  Use Gparted to split your hard drive in half and install XP on the front and use ubuntu on the 2nd half.  The ubuntu installer will take care of setting up the bootloader.

---

### Post by gilloz on 2008-11-09
I have dual boot with Windows XP and Ubuntu, but they say that you should have Windows installed first and then you install Ubuntu.  For me, I have two hard drives (80GB), one with each of the OS's.  When you load Ubuntu, it puts the Grub bootloader on MBR to give you the menu to choose which OS to run. It worked out good because just recently I had a major fatal failure with my Windows XP and could no longer open it, but I still had access to Ubuntu, email and the Internet.  Having both OS's on the same drive could cause you a problem should you lose access to that drive. Anyway, that is my experience.  I am sure there are those that will disagree with that.  BTW, once you have Windows XP installed, I use the Disk Management program in Windows to set up my partitions on the second drive prior to installing Ubuntu.  Did not have to use Gparted.  Take a look at this link:  

[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)   Good Luck

---

