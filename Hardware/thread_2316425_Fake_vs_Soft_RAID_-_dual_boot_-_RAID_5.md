---
title: "Fake vs Soft RAID - dual boot - RAID 5?"
date: 2016-03-08
forum: Hardware
---

### Post by josh168 on 2016-03-08
Ultimately I just want to know the best&#8482; way to create a dual boot environment, which isn't installed on a RAID array but does include an array. I want to mount my home directory on the array in fact, and possibly /usr/ also. Windows 10 will *definitely* have data on the array, more than likely a few hundred gigs of games.

I am working with an ASUS Sabertooth 990FX motherboard. The fakeRAID is detected as promise fasttrack, which does not support level 5 RAID. I am shooting for RAID 5, simply because I had a drive fail and I can't afford to replace it. My system configurations are up in the air until I can resolve this. Last week I decided to clean install Windows 10, and now that I've got that sorted out - I even made an autounattend.xml answer file to aid me in my journey - I am ready to create a dual boot system. I need to know how to go about my RAID array configurations though. 


[LIST]
[*]Can I have it fakeRAID in windows and softRAID in linux?
[*]Or perhaps I should suck it up and use RAID 1 instead?
[*]Or maybe, since I don't really need even a full TB, I could somehow hack together a RAID 0 using 2 drives at a lowered capacity, and then mirror that array against the slowest drive of the three using software?
[/LIST]

Is it possible for me to manually build a RAID 5 array inside linux, using mdadm or anything else, when the array is "natively" fakeraid(which would make it softraid in linux and fakeraid in windows, right?), and thus undetectable via dmraid?

I have $0.00 to spend, so I need a solution that will cost me time and effort. I just want to utilize as much storage space as I have available, with my partitions.. and not necessarily my data. A solution which provides me some redundancy is preferred, and I would really like to have a hdd performance boost as a result; definitely not a performance cost to the drives.

My drives are as follows:
[LIST]
[*]Seagate 1TB - 6Gbps
[*]Seagate 1TB - 6Gbps
[*]Hitachi 1TB - 3Gbps
[/LIST]

What are my best options here? Looking for opinions, and suggestions. Or outright be-all-end-all solutions. Which cost my wallet nothing.

---

### Post by TheFu on 2016-03-10
While it might be possible, I wouldn't mix partitions between Windows and Linux RAID.  The drivers are different and with each update, there is an incompatibility risk.  That could lead to data corruption that wouldn't be reported. Rather, create 2 partitions on the disks - a) for Windows, b) for Linux, then use whatever software RAID you like on each OS. Do not mix. If your data is important enough for RAID (which is only really useful for HA or performance reasons), then it is important enough to was storage to avoid possible corruption.

I cannot think of **any** reason to ever use FakeRAID.  It has all the limitations of HW-RAID (mainly being tied to the HW) without the performance. SW-RAID is much more flexible and I've moved SW-RAID arrays across 3 very different machines - never lost a bit.  Do that with different motherboard-RAID setups - not likely.

However, RAID never replaces backups, so if you don't have backups, forget the RAID stuff completely.  Writing corrupted data in 2 places fast is what RAID alone can do. Only a backup will be able to correct that, provided it is versioned.

Just because something can be done, that doesn't make it a good idea.

And welcome to the forums.

---

