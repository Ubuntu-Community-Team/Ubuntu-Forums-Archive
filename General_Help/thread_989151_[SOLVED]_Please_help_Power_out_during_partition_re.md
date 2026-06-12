---
title: "[SOLVED] Please help: Power out during partition resize (Ext3)  - can files be saved?"
date: 2008-11-21
forum: General Help
---

### Post by LeSid on 2008-11-21
Hi all

I shrank an ext3 partition with gparted when the impossible happened: Power went out. (I thought this happened once in 5 years in Switzerland). The laptop continued to run on battery but the USB drive was powerless for a minute. 

gparted had said before it happened that the process was at the stage of copying blocks and would take another 4 hours (ca. 300 GB of data on a 500 GB disk). 

When the disk had power again, gparted showed that it had the size it was supposed to have after the shrinking, but no data was detected (capacity/usage).

I didn't mount the partition at any time, so there should not have been any writing. 

So, now is there a way to recover some of the data? 

I'm trying to work from the console. Since I realised that checking the file system etc. can take a very long time and I hooked up the disk to my NAS that runs OpenWRT (I still post the question here in the ubuntu forum, not because it was while using Ubuntu that it happened, but because I believe the solution, if there is one, might be quite linux generic and I could shutdown the laptop while the NAS runs the checks etc.) If any suggestion can't be followed in OpenWRT, I'll hook up the disk back on the ubuntu laptop. 

An fsck on openwrt shows the following output ("movies" is the disk's label):

```
root@OpenWrt:~# e2fsck -n -v /dev/sda1
e2fsck 1.39 (29-May-2006)
movies contains a file system with errors, check forced.
Pass 1: Checking inodes, blocks, and sizes
Error allocating block bitmap (1): Memory allocation failed
e2fsck: aborted
```

Thanks for any assistance!
LeSid

---

### Post by caljohnsmith on 2008-11-21
Really sorry to hear of your partition fiasco; I would try using "[photorec]("http://www.cgsecurity.org/wiki/PhotoRec")" to recover your data. It is part of the "testdisk" package in the repositories. Let me know how it goes, and best of luck recovering your files.

---

### Post by LeSid on 2008-11-21
Thanks, I'll try that and report back.

---

### Post by LeSid on 2008-11-24
Photorec worked quite nicely, thanks for the tip!

---

### Post by blazemore on 2008-11-24
Say Thankyou and mark as solved, LeSid
thx :)

---

