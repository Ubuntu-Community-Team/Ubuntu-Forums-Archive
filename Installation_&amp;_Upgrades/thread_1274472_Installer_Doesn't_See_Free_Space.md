---
title: "Installer Doesn't See Free Space"
date: 2009-09-24
forum: Installation &amp; Upgrades
---

### Post by beartofear on 2009-09-24
Hi everyone, 

I'm trying to install Kubuntu 8.04 (64 bit) on a computer at work.  I used the Windows Disk Manager to Shrink the Vista Partition and leave ~400 GB free space on the TB HDD to install Kubuntu.  When I boot from the CD to install, there is no detection of the free space from the hard drive.  Kubuntu wants to repartition the space left to Vista, or if I check largest free space it sees none.  I did not format the unallocated space after using the Vista disk manager. 

Hopefully someone has some suggestions here. 

Thanks!

---

### Post by Bucky Ball on 2009-09-24
Does Vista show it as free space in Disk Management?

Dumb question but just checking. ;-)

---

### Post by beartofear on 2009-09-24
Actually yes it does ... 

Under management I have

Disk 0:  EISA (71MB) D: Recover (15 GB) C: OS Vista (495.47 GB) and then 420.97 GB of Unallocated Space ... which is to be Kubuntu's home.

---

### Post by Bucky Ball on 2009-09-24
Hmm, yes. My advice would be to back up the recovery partition so you have a working Windows install disk (the manufacturer probably gave instructions on how to do this) and wipe the drive and get rid of that EISA partition and everything else!

Re-install Windows, creating only the partition it needs to go on in the process leaving the rest free space (ie delete any other partitions the Windows install sees) and then install Ubuntu on the free space using manual partitioning or what ever you fancy when it gets to that part of the install.

For some reason computer manufacturers figure it is more efficient to stick your Windows install disk (a legal requirement) on the first partition of the first hard drive, the fastest bit! Then it is up to you. If Windows crashes and you haven't got a backup of this bit you're screwed unless you could be bothered explaining it to the computer manufacturere but they don't always make that clear.

---

### Post by beartofear on 2009-09-24
Well, there's now two issues here.  

1)  I was hoping since I did a lot of work to get the Vista side of things running that I wouldn't have to wipe the HDD and start over at this point - maybe there is a work around?

2)  I did receive a "reinstallation" DVD from Dell with the computer.  If have that I gather I don't need the recovery drive?

---

### Post by Bucky Ball on 2009-09-24
Part two exactly. You don't need the recovery drive. 15Gb of wasted space on the fastest part of the drive. Beats me why they do that.

When I got my laptop I backed up the recovery partition twice then wiped the drive and re-installed Vista (Ugh but believe it or not HP and MS won't let XP run on my laptop) then Ubuntu and sweet two and a bit years later. No wasted space.

The workaround would be to get into vista and delete all the partitons BEFORE the vista one making it into free space. Then while still in vista expand the vista partiton into that free space (good idea to do a defrag first-recommended).

---

### Post by rreese6 on 2009-09-24
One Question,
Couldn't he just use gparted to partition the free space Vista made?

---

### Post by Bucky Ball on 2009-09-24
> **rreese6 said:**
> One Question,
Couldn't he just use gparted to partition the free space Vista made?

Yep. But then you need to set up grub because Windows will complain unless it thinks it is on first primary partition, first physical hard drive.

---

### Post by beartofear on 2009-09-25
I managed to get this all up and working and resolved - and I even freed up that "faster" part of the drive.  Thanks for the help guys.

---

### Post by rreese6 on 2009-09-25
I see you got it resolved. Please post how you did so others may be helped. Then change the post to solved.

---

