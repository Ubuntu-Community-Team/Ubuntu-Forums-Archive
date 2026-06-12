---
title: "Hard drive Mounting in wrong location and not mounting period"
date: 2013-04-16
forum: Hardware
---

### Post by snuffy47 on 2013-04-16
Hello

Few days ago had to restart my computer running 12.04 ubuntu that I use as a storage server for my home movies and other odds and ends

It has a Raid 6 array and 3 other drive 2 1TB abd 1 2TB

After the restart I got an error at the splash screen that Server_Raid6 was unable to mount s for skip or Manual.  After doing a repair in Disk Utility I could mount it but it will not mount were I set it too in fstab

Now I was backing everything up too my other drive as I had a sinking feeling another freeze up and after a restart now one of the 1TB drive and the raid were stating that they were unavailable at the splash screen and when I got logged in the 1TB drive was mounted were the 2TB should have been

Kinda at a lose here on were to start please help.

My operating system is on a separate 500G drive from these

---

### Post by ahallubuntu on 2013-04-16
~

---

### Post by snuffy47 on 2013-04-16
Okay the !TB drive that just started the Not ready yet or not available at the splash screen has a Reallocated Sectors Warning at 29 sectors.  How do I fix it I cannt see any repair function and it is currently mounted in the wrong location

The Raid6 array is resync at the moment so cannt really do anything

---

### Post by ahallubuntu on 2013-04-16
~

---

### Post by snuffy47 on 2013-04-17
Okay guess I will just stop untill i can get some drives to back some of this stuff up

So looking things over I have a single 1TB drive with that warning but my Raid Array Drives show clean.  Still doesnt explain the problems with mounting in wrong location or not mounting at all with the RAID drives.  

I used UIIDs in fstaba

Also the single drives are NFTS and the Raid is EXT4

Should I just format drives to EXT4 when I get thing backup?  Reason I used NFTS was incase I needed to use a windows machine to access the drives at somepoint but I guess really I could always use a live cd or install ubuntu beside any windows system.

Any advice here would be appreciated.

---

