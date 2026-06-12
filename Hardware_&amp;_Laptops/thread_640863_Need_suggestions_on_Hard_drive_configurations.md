---
title: "Need suggestions on Hard drive configurations"
date: 2007-12-14
forum: Hardware &amp; Laptops
---

### Post by tuproxy on 2007-12-14
I finally decided to build a new server/desktop PC and need some suggestions on the hard drive setup

Here is the new system:
Abit IP35 Pro 775
Intel Dual Core E6750
4 x 1Gb PC6400 Corsair RAM
FXF PCI-X 8600

The MOBO has 6 on-board SATA II ports that support RAID0/1/5/10

Here are the other drives that I have available
2  74GB SATA I Raptors (Western Digital)
2  36GB SATA I Raptors (Western Digital)
2  250GB  SATA II WD's
3  500GB SATA II (Western Digital)
1  500Gb SATA II (Seagate)

My plan is to install 6.06 64-bit and run VMware server where I am going to be running XP, 2003 server and other Linux Distros.

I may have 3-4 vitrual systems running at a time, so I'm not sure what the best setup would be. I was thinking of running RAID 0 on the 2 74's and the also running the 2 36's in RAID 0 as well.  I'm concerned with one of the drives going down so I thought about backing up the two stripped sets to one of the 250's.  Would this be a good setup or can someone think of a better array?

BTW, the 500's will probably not be running RAID. They will be on a separate SATA controller.

Opinions and suggestions are greatly appreciated!

---

### Post by jbulcher on 2007-12-15
How important is uptime to you? If you want speed more than you need uptime, then RAID0 is fine. You *could* get two more HDs and set up RAID 0+1, although if you were going to do that RAID 1+0 would give you better redundancy if it takes more work. It doesn't sound like you want to do that though,

Otherwise, if you need uptime more than reliability, you need to set the disks up in a RAID 1 configuration and take the space hit. Any other option (i.e. RAID 5) will require more partitions/disks.

---

### Post by Rupertronco on 2007-12-15
Raptors are pure performance drives, I wouldn't use more than two in one rig. They're only really viable for your OS/Applications. Do you have another rig you could put the 2 36gig raptors in to maybe up its performance a bit? I think it'd be a waste of their speed to have all 4 in one setup. I'm currently running 2 raptors in Raid 0, but the performance increase vs. risk is just nonsensical, so I'm seriously considering going raid 1 with them. 

As far as the 500gb  drives, a raid 5 array would work nicely to give you some additional data security. Is any of your data irreplaceable or mission critical? If so, I'd consider a raid 5 array on the storage drives. 

Just out of curiosity, what case do you have? It's going to weigh a ton by the time you're done with it!

---

