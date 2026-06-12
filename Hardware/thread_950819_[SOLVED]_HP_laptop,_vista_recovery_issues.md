---
title: "[SOLVED] HP laptop, vista recovery issues"
date: 2008-10-17
forum: Hardware
---

### Post by Helios1276 on 2008-10-17
Long story short-ish, having been on the phone with HP and trying a few things myself, I am having some trouble re-installing Vista with the recovery disc I made upon purchasing the laptop. The disc errors at 55% while trying to format the drive (error 0x 400 100 130000 1002).

Checking things in Gparted I notice there is still a remaining HP Recovery partition (11gb). After trying a few more times I thought I would try wiping the drive under the assumption the recovery partition was conflicting with the recovery disc. Wiped the drive with Dban but the recovery partition remains.

 I was sent a program by HP support , I think it was called deldelete? But my college email is down for the last few days due to spammers I can't obtain it. 

(this is not a thread to discuss the cons of Vista ;))

---

### Post by LaRoza on 2008-10-17
It could be a hard drive issue. It could also be a disk problem.

I don't know how much help we can be. I personally would try to swap the drive to see if I get the same error, but I am not sure how recovery systems take to that.

---

### Post by Helios1276 on 2008-10-17
> **LaRoza said:**
> It could be a hard drive issue. It could also be a disk problem.

I don't know how much help we can be. I personally would try to swap the drive to see if I get the same error, but I am not sure how recovery systems take to that.

Would the fact that I was able to install Heron with no issues on the drive narrow it down?

---

### Post by submain on 2008-10-17
If you want to wipe out everything, try formating each partition and then excluding all partitions using something like fdisk. You could also use ubuntu boot disk, I guess that would be easier...

---

### Post by Helios1276 on 2008-10-17
> **submain said:**
> If you want to wipe out everything, try formating each partition and then excluding all partitions using something like fdisk. You could also use ubuntu boot disk, I guess that would be easier...

I've attempted to format/destroy the partitions on a few occasions using gparted and Dban. I'm not sure I fully understand what you mean by 'excluding' the partitions with Fdisk.

I'd be interested to track down this Deldelete program that was mentioned to me but have had no luck thus far.

---

### Post by Helios1276 on 2008-10-18
Bump, also the program is called Deldisk but it was no help.

---

### Post by Helios1276 on 2008-10-21
Bump, has no one encountered this issue?

---

### Post by Helios1276 on 2008-10-24
Solution: Annoy HP until they send you the disc.

---

