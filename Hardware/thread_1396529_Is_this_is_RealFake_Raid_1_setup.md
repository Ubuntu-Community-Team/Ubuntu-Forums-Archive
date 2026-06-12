---
title: "Is this is Real/Fake Raid 1 setup"
date: 2010-02-02
forum: Hardware
---

### Post by AmbiguousOutlier on 2010-02-02
[http://europe.giga-byte.com/FileList/Manual/motherboard_manual_ga-ma780g_ud3h_e.pdf](http://europe.giga-byte.com/FileList/Manual/motherboard_manual_ga-ma780g_ud3h_e.pdf)

On page 75 it starts talking about setting up RAID 1. If I do this will it just work and boot straight into ubuntu?

I have 3 SATA drives, 500gb which contains my OS partitioned to 50gb and 450gb. I don't want this drive to be on the raid. I'll back up the 50gb via some other method to restore the OS (I haven't figured that out yet, that's next weeks job to research). The 450gb will just be temp area and I don't care if that data gets lost.

I then have 2x 1tb drives. I want these to be mirrored. However they both contain data. In total it is around 500gb. 

From what I read in the above pdf, it wants to delete all data on my disks. And I think it wants me to install an OS on it. 

I've never done anything with RAID before.

Can someone tell me what my options are?
Thank you.

---

### Post by zwaardmeester on 2010-02-02
afaik, creating a raid setup will destroy all existing partitions and data on the disks.

---

### Post by AmbiguousOutlier on 2010-02-02
I could probably back up the data, and copy it back on.

So if I go through the Bios settings route. This will be a fully functional hardware RAID?

---

### Post by zwaardmeester on 2010-02-02
What makes you think it is not a fully functional RAID setup? Like it says on page 10, 
```
Support for SATA RAID 0, RAID 1, RAID 10 and JBOD
```
I expect nothing less than full hardware RAID. But then again, my opinion and i'm not an computer engineer.

---

### Post by AmbiguousOutlier on 2010-02-02
> **zwaardmeester said:**
> What makes you think it is not a fully functional RAID setup? Like it says on page 10, 
```
Support for SATA RAID 0, RAID 1, RAID 10 and JBOD
```
I expect nothing less than full hardware RAID. But then again, my opinion and i'm not an computer engineer.

It's just everywhere I've read suggests most hardware controllers on motherboards are no true raid and that you also need some kind of software to actually control the raid. The hardware just helps out a bit.

But if you think I wont need to do anything with the software, I'll go ahead and switch it on.

---

### Post by pirateghost on 2010-02-02
raid built into motherboards is almost 99.9999% "fakeraid"  they are really no different than buying the cheap "raid" cards that cost less than 30 bucks.

even if you enable raid1 on the mobo, you will still probably see the drives as separate disks in linux.

i say use the software raid in linux, if the motherboard ever dies, it wont matter what machine you swap the drives into, you can still access them from another linux box.

---

### Post by AmbiguousOutlier on 2010-02-03
I set the raid up on the motherboard, and linux can only see one drive. So I have that 0.0001% of motherboards with real raid. Awesome.

---

