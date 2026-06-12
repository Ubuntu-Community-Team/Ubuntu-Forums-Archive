---
title: "Corrupt Partition"
date: 2008-07-02
forum: Hardware
---

### Post by MET920 on 2008-07-02
A friend of mine gave me her hard drive (we'll call this one HDD1) because the C: partition which had Windows XP (the only OS she had installed) got corrupted.. She said she had taken it to 2 shops for data recovery and both weren't able to access the data on HDD1.. One of the random tests I did was run my Ubuntu 7.04 Live CD on her computer and I was able to access all the files on her C: partition..

I removed HDD1 put in another one (we'll call this HDD2) in her computer to install Ubuntu on it so I can copy the files over.. The installation worked.. But after installing Ubuntu and running from HDD2 and re-inserting HDD1, the computer no longer detected HDD1.. I'm not that experienced with Linux, but iirc other HDD's would show up in computer and then all you have to do is to mount the disk by double clicking it.. The only things I found in computer were filesystem, CD/DVD-ROM and the floppy drive..

So question 1: Am I doing something wrong with mounting the other harddrive? If so, what am I doing wrong and what do I need to do?

Next problem.. I decided to try the Live CD again, but while it was booting Ubuntu from the CD, I got the following error(s):
```
BusyBox v1.1.3 (Debain 1:1.1.3-3ubuntu3) Built-in shell (ash)
Enter 'help' for a list of built-in commands.

/bin/sh: can't access tty: job control turned off
(initramfs)
```

Question 2: What does that mean? And why isn't it working now, when it was working earlier when I installed Ubuntu from the CD? What do I need to do to get the Live CD to work again on that computer?

Thanks a lot in advance for your help.

PS. and this may sound kind of random: I have 2 Ubuntu Live CD's (a 32-bit and a 64-bit) because a local computer shop was giving them out. I've used both several times on other computers so I know they work. On her computer, I got the above mentioned error when inserting the 32-bit CD for the first time. The 64-bit one worked so I installed that. I stupidly forgot the password I put on that computer so decided the easiest thing was to just format it again. When I decided to do that, I started getting the error above with the 64-bit CD, but the 32-bit one worked. So I installed the 32-bit one. When I mentioned I got the error above, that was after the installation of the 32-bit CD. I tried both CD's after that, but neither works, but they both work on my computer :-/

---

### Post by logos34 on 2008-07-02
> **MET920 said:**
> I removed HDD1 put in another one (we'll call this HDD2) in her computer to install Ubuntu on it so I can copy the files over.. The installation worked.. But after installing Ubuntu and running from HDD2 and re-inserting HDD1, the computer no longer detected HDD1.. 

If these are IDE disks (not sata), then maybe the jumper on the back of the hdd1 is incorrectly set.  If you are plugging it into the same ribbon cable as hdd2 (gray connector on cable?), then you probably need to set it for 'slave'.  The black connector is master.

Or else set them both to 'cable select'

---

### Post by MET920 on 2008-07-02
HDD2 is IDE while HDD1 is SATA, but I thought that was irrelevant.. Do I need to remove that little white plastic thing that's on 2 of the pins?

---

### Post by logos34 on 2008-07-02
> **MET920 said:**
> HDD2 is IDE while HDD1 is SATA, but I thought that was irrelevant.. Do I need to remove that little white plastic thing that's on 2 of the pins?

no leave the jumper on the ide because it works...sata II's have jumpers but that's for backward compatibility with sata I-only boards.  

Does HDD1 at least show up in the Bios?

---

### Post by MET920 on 2008-07-03
yeah

---

### Post by logos34 on 2008-07-03
well, if the Bios sees it but doesn't show up in linux with **sudo fdisk -l **or **sudo lshw -C disk**, then I don't know what to suggest...maybe try a different sata channel/port on the board, but I doubt that will help.  Or maybe try different sata modes in the Bios (if applicable)...raid should be disabled

---

### Post by MET920 on 2008-07-04
> **logos34 said:**
> well, if the Bios sees it but doesn't show up in linux with **sudo fdisk -l **or **sudo lshw -C disk**

Oh I didn't try that.. I don't really know much about Linux.. I'll try that now.. I just tried opening Places>Computer which should normally show other HDD's that are connected to the computer..

I just tried it now and only got 1 HDD which is the one I'm running Linux from, but I didn't get the SATA HDD -.-"

> **logos34 said:**
> maybe try a different sata channel/port on the board, but I doubt that will help.

Just tried this, but no difference..

---

