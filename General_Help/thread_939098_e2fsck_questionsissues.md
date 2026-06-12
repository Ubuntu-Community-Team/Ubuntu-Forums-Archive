---
title: "e2fsck questions/issues"
date: 2008-10-05
forum: General Help
---

### Post by Kehnoo on 2008-10-05
I'm running Ubuntu on my fileserver box. I set up a nice RAID5 with 6 disks and now I've been growing it with a few extra disks.

I did have issues with mdadm - the mdadm shipped with ubuntu was old and I had to compile a new one from the Internet to get the grow/add work.

To run e2resize I need to run e2fsck. I ran it for 3 days. The process didn't have any movement on program top (as in the mem/cpu% etc were stuck) so I killed the process and started to wonder if
1) the fsck was actually doing something but very slowly. There were reports on the Internet saying that it could take several days on large RAID arrays. I ran it with 'e2fsck -v -y -B 4096 -f -b 163804' 
2) the fsck was stuck, but why? There wasn't anything on 'dmesg' other than normal stuff. The process didn't print anything out of ordinary. 

The box is now running badblocks on the raid drive as one chap on the IRC suggested. I tried to mount the raid array and it mounted okay and I had my files readable.

My hardware is 
AMD Athlon X2 2,5 GHz
abit NVIDIA 8200 Motherboard
3 GB of RAM
2 Silicon Image SiI3132 controllers
9 Western Digital 750 GB  
Ubuntu 8.04 i386 livecd on USB flashdisk

---

### Post by nowshining on 2008-10-05
did u unmount the disks before running e2fsck on them??

---

### Post by Kehnoo on 2008-10-06
> **nowshining said:**
> did u unmount the disks before running e2fsck on them??
Yes, I have it unmounted as I'm running the e2fsck from live cd.

Badblocks didin't retunrn any bad blocks.

---

### Post by Kehnoo on 2008-10-06
The fsck seems to always crash/get stuck on same place, with following line:

Clone multiply-claimed blocks

and with -y parameter the fsck will try to do it but gets unresponsive as killing it with regular kill/or ctrl+c doesn't work.

---

### Post by fjgaude on 2008-10-06
Maybe fsck doesn't understand the huge size of your array... all these big drives are relatively new to our world.

What does

```
sudo mdadm -D /dev/md[n]
```

show?

---

### Post by Kehnoo on 2008-10-06
> **fjgaude said:**
> 
What does

```
sudo mdadm -D /dev/md[n]
```

show?
I can't do copy/paste but I'm not seeing anything out of ordinary. The superblock is persistent and all drivers are in use and the array is clean.

Size of the array is 5851900416 (5580.81 GB 5992.35 GB) but I'm only using 3,2 GB of it as I haven't been able to resize it - I have to run fsck first.

---

### Post by fjgaude on 2008-10-06
You mean when you run resize2fs you get an error message, eh?

That didn't work, eh? I think maybe resize2fs doesn't understand a 6TB array. Maybe a bug report is in order?

---

### Post by Kehnoo on 2008-10-06
> **fjgaude said:**
> You mean when you run resize2fs you get an error message, eh?

That didn't work, eh? I think maybe resize2fs doesn't understand a 6TB array. Maybe a bug report is in order?

resize2fs suggested that I should run e2fsck. I don't think I should risk loosing 3 TB worth of data without running it first. Shouldn't filesystem health always be the first priority?

I have ran fsck on the 3,2 GB partition before, it's just that it decided to break now.

---

### Post by fjgaude on 2008-10-06
Well, run it... on an unmounted array.

**All this points to the importance of having a backup, I have three, one online, one near-line, and one offline.**

Let us know what happens.

---

### Post by Kehnoo on 2008-10-07
Tried running e2fsck from x86_64 8.10 beta live cd, no luck. Still gets stuck on the same spot.

---

### Post by fjgaude on 2008-10-07
Don't know what to suggest...

---

### Post by Kehnoo on 2008-10-07
Tried Gentoo LiveCD, no luck either. So it's not related to Ubuntu. I'll probably get the data out and install clean OS on it.

---

### Post by fjgaude on 2008-10-07
Sometimes that's what it takes, a clean install... thus is the reason for always, always having good backups to important data. I keep three, online, near-line, and off-line.

---

### Post by rbroderi on 2008-10-11
ran into a similar problem.  e2fsck can take a long time to clone blocks.. ie (>72 hours for my 750GB drive) so I think you would just have to wait a long time plus you need to be running it from a 64 bit kernel and have lots of swap mine is using over 16GB of ram+swap

---

