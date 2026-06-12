---
title: "Fake RAID Drives not recognized by Ubuntu"
date: 2011-04-19
forum: Hardware
---

### Post by wghoward on 2011-04-19
I have a Asus P7P55D-E LX motherboard that has 1 x 250GB HD for the OS and 4 x 2 TB HD's configured as RAID5 (parity) - 4.7 TB for data storage.  

I have been trying to install either Ubuntu 11.04 or 10.10 to use the system mainly as online data storage for photos/videos (backup to external drives done separately).  Both OS's load successfully but the OS is giving me fits trying to partition/mount the data drive.

What is very strange is that I am seeing very inconsistent and unreliable behavior - somethings the 4.7TB drive is recognize and I can look at with parted, qparted, qdisk, dmraid without an issue but then after a reboot the directory /dev/mapper shows:
  *  isw_dhidjaebdd_Volume0
  *  isw_dhidjaebdd_Volume0_err_target
The volume is no longer visible and qparted (and other programs) seem to have lost their partition information.

I have tried configuring the volume as RAID 10, RAID5 with various stripe sizes - all with same results.

I have read through many many posts/google searches about "fake raid", GPT, dmraid, etc, etc but nothing that seems to indicate why either Ubuntu 10.10 or 11.04 should have a problem consistently recognizing the large HD using GPT.

Has anyone else seen this and found a way to get the drive recognized/formatted and consistently be recognized between reboots?  I have considered software RAID but would like to know if this is possible or of Ubuntu (or linus distros) in general, can't handle HDs > 2 TB at this point.  

Any help resolving this would be greatly appreciated - direct msg or public replies are welcome.

Thanks in advance.

---

### Post by srs5694 on 2011-04-20
If the computer is to boot Linux *only*, then Linux's own software RAID is definitely preferable to motherboard-based software ("fake") RAID. Use Fake RAID only if you must use the RAID configuration across multiple OSes (normally Linux and Windows).

As to the problem itself, my guess is that it's a race condition of some sort -- perhaps the RAID software is trying to initialize before the drives are ready, or maybe the drives' IDs are changing from one boot to another and causing confusion. This tentative diagnosis is moot if you switch to Linux's own software RAID, though, since it's an entirely different software stack that might not have the same problem.

---

### Post by donarntz on 2011-04-20
I've been unsuccessful getting my raid10(containing my music files) to automount at boot.  It hits the "wait, skip" screen every time unless I put "nobootwait" in the fstab.  Its a pain.  I'm really not happy about it.

---

### Post by wghoward on 2011-04-21
srs5694,

Thanks for your response - It made me go take a deeper/second look at what Linux was telling me in the logs.  Briefly - here is what I found in dmesg:
* The array is 4 drives - drive /dev/sda, sdb, sdc all get initialized by the OS.  Immediately after sdc is initalized, dmraid starts. It detects that the RAID array is degraded (because sdd has not started yet) and then essentially gives up and makes the array inaccessible.

I tried to reduce the number of disks to 3 just to see what would happen and it was more consistently making the RAID array available to me but after what I saw in the logs, I wasn't going to temp fate that it would start up properly everytime.  Further, I have the 4 disks and would like to take advantage of the extra space.

What I surmise is that either, A - there is a bug in the dmraid or there is a disconnect on how linux starts up that doesn't give the drives enough time to be initialized by the OS.  The other idea may be that the code didn't consider 4 or more disks as much of an option.  Either way - this is too unreliable to risk the data on.

From what I gathered by reading more about Fake RAID vs. OS - it appears they are essentially the same thing since the OS/drivers are handling the RAID management as opposed to true hardware based RAID card.  Definitely wasted far too much time wrestling with this for no real advantage (no I won't be dual-booting windows).

I am in the process of creating the array from linux - so far so good.  Would like to have had the ability to create it during OS installation (wanted my /home dir on the RAID drive) and more GUI based tools but one can't have everything ;)

I will finalize this post if I my testing is successful - thanks again for the input.

---

### Post by wghoward on 2011-04-26
Well the long/short is that, while it is not GUI based, once the OS based raid is setup, it is working along without any issues.  The only hiccup is after a reboot, the raid drives went from being /dev/md126 and /dev/md127 to /dev/md0 and /dev/md1.

Does anyone have an throughput #'s for what a decent raid array should be able to read/write?

---

