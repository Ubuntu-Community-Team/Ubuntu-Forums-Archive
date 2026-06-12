---
title: "Risk Assessment? Change NTFS Disk Partition Size"
date: 2009-05-05
forum: Hardware
---

### Post by Ciridan on 2009-05-05
Hi Folks

I have a Compaq 8510W notebook and the "smart" people here configured the drive to only have a 20G primary partition for running XP.

I regularly run Ubuntu in a VM and also from the live CD  (8.10).  I know I can manage partition sizes on HPFS/NTFS partitions from the live Cd.

So my question is how difficult is it and how risky is it to take some space back from by D:  drive partition and add it back to my C:.  I have 8.82G free on D right now and can free up more, but only 1.49G available on C:\

I need to be careful and I do backup etc. but I really don't want to end up blowing away the primary WinXP partition.  I would likely have much work to do and possibly some explaining.  
However I can't think of any sane person thinking WinXP with a full Office install and other corporate crap would live for long in a 20G drive.

I appreciate any words of wisdom!

Thx.

---

### Post by gordintoronto on 2009-05-05
You could probably achieve your objective by moving the Windows swap file and Explorer's cache.


> **Ciridan said:**
> Hi Folks

I have a Compaq 8510W notebook and the "smart" people here configured the drive to only have a 20G primary partition for running XP.

I regularly run Ubuntu in a VM and also from the live CD  (8.10).  I know I can manage partition sizes on HPFS/NTFS partitions from the live Cd.

So my question is how difficult is it and how risky is it to take some space back from by D:  drive partition and add it back to my C:.  I have 8.82G free on D right now and can free up more, but only 1.49G available on C:\

I need to be careful and I do backup etc. but I really don't want to end up blowing away the primary WinXP partition.  I would likely have much work to do and possibly some explaining.  
However I can't think of any sane person thinking WinXP with a full Office install and other corporate crap would live for long in a 20G drive.

I appreciate any words of wisdom!

Thx.

---

### Post by Ciridan on 2009-05-07
Thanks Gord - great suggestions.

That will take care of my immediate problem.

I'm still curious if this is a valid approach if I run out of disk in future.

Anyone have any experience with changing Windows partition sizes with a live CD?

---

### Post by odinb on 2009-05-07
Just download a gparted disk image and burn it, and boot/do it from that...

Has worked for me in the past, except for an HFS+ partition that I could only make smaller, I wanted to make it bigger...

Depending on the operation, it may be time-consuming if it has to move lots of data, but it has worked flawless for me on both EXT3 and NTFS!

---

### Post by brokenwindows on 2009-05-07
Have you at least tried to run the partition compressed? It won't give you a ton more space, it will help though. There is free partition software out on the internet. Before I got my new hard drive I had to do what you want to do. I had no problems changing partition sizes multiple times. I finally gave up and bought a new drive...

---

### Post by Ciridan on 2009-05-08
Hi Folks

Thanks!  I don't really want to run the drive compressed - performance issues and I'm stuck with my drive as this is a work computer.

Is gparted on the live CD?  I believe I need to move space from a D: partition and want to add it to the C: boot partition.  I don't believe there is any allocated space on the drive itself.

Any pointers to documentation or anything else I need to be aware of?

Thanks to all

---

