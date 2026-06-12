---
title: "Win 2000/ubuntu 8.10 dual boot !"
date: 2009-04-23
forum: Installation &amp; Upgrades
---

### Post by sailthesea on 2009-04-23
No doubt everyone is trying out Jaunty today but I'm still trying to get Intrepid into this old Dell with Win2000 on it
 I've got 82% of the disc clear but I'm left with 2 unmovable blocks of files high up in the drive Most of the threads I've searched so far are too out of date to help me... 
 So :
 Can I find out what they are and move them forcibly, With Win or from the LiveCD?

 Could they be left over from the Wubi install I deleted?

 I would be very grateful if any one has the time to give me a tip!
 Thanks:)

---

### Post by sailthesea on 2009-04-23
Please?:(

---

### Post by Ugluk on 2009-04-23
It's probably MFT. It should be sorted out by resizing patrition. Why are you not happy with WUBI install?

---

### Post by sailthesea on 2009-04-23
Wubi worked great but I want the experience of setting dual boot with Ubu and to see how it runs in its own enviroment
 What is MFT?  I'd like this to work and understand what I'm doing, manually partioning a drive is pretty new to me

---

### Post by sailthesea on 2009-04-24
If I move try to move these files when partitioning will they be destroyed? I can't see GParted rewriting the Windows FAT

---

### Post by sailthesea on 2009-04-25
HI all! Hows Jaunty playing?
 I still can't fix this problem with Windows system files blocking my drive out I don't think Gparted will be kind to them if I make a new partition and shrink win down past them 
 Or would Gparted let me fix this later if I installed in the clear space?
 Am really stuck on this I don't have any facility to move them

---

### Post by meierfra. on 2009-04-25
> If I move try to move these files when partitioning will they be destroyed? 
No. Those blocks should not cause any problems. Also gparted does a read-only practice run before it does the actual resizing. So if gparted will detect any problems before the resize.   But of course you  should backup any valuable data before you do any partitioning.

---

### Post by sailthesea on 2009-04-26
> **meierfra. said:**
> No. Those blocks should not cause any problems. Also gparted does a read-only practice run before it does the actual resizing. So if gparted will detect any problems before the resize.   But of course you  should backup any valuable data before you do any partitioning.

 Copy that Thanks I'm a bit nervous about this kind of thing 
 The disk continuity that linux seems to use is a bit new to me but it seems stupid to do it any other way now! 
 Time to give it a go!:)

---

