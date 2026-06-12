---
title: "Ubuntu showing RAID1 as 2 drives?"
date: 2009-12-26
forum: Hardware
---

### Post by nemesis99 on 2009-12-26
I'm in the process of building a simple server with an Adaptec 1220SA RAID card. I have two 320GB drives configured in a RAID1 array on the card itself. When I load a live cd of 9.10 (32bit), GParted sees two drives, /dev/sda1 and /dev/sdb1. I'm confused here. How is the live cd seeing the two drives? I've always been under the impression that the RAID card will present a single logical disk to the OS based on the way I configured it.

---

### Post by pastalavista on 2009-12-26
I'm not sure, but from what I understand, isn't Raid0 supposed to be the single drive config? I thought Raid1 was for mirroring the two drives. Maybe I have it backwards.. I've never used raid.

---

### Post by PilotJLR on 2009-12-26
You're seeing the two disks because these RAID controllers use what most people call "fakeraid" to present the RAID volumes to the OS. Fakeraid relies on software to perform the RAID operations... more expensive server class RAID cards (most are several hundred dollars at the minimum) will perform all RAID operations in hardware. For example, these server class cards will perform RAID 5 XOR operations using ASICs in the board itself, which removes the need to perform this work on the machine's CPU.

My personal preference is to use mdadm instead of fakeraid, but either is certainly an option. With mdadm, you have no dependencies on the controller whatsoever, so you could change hardware as much as you want without trouble. It's something to consider.

---

### Post by PilotJLR on 2009-12-26
Also - good info here:  [https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto)

---

### Post by nemesis99 on 2009-12-26
Thanks for the info.  Looks like I will toss this RAID card in the junk drawer and use something more preferable to linux.

---

