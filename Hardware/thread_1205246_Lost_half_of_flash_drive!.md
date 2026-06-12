---
title: "Lost half of flash drive?!"
date: 2009-07-05
forum: Hardware
---

### Post by Vrekk on 2009-07-05
Hi the other day I pluged my flash drive into my computer and tried to copy a 1.2 gb file onto it, but i get an error saying that there is not enough space on the disk.  So at first im thinking i have another file on it so i open it up and its empty (I even checked the .trash files).  When I plug it in Ubuntu mounts it as a 2gb Media, but it only says 945mbs are there.  I even removed the drive and it says 2gbs right on it, so that not the issue. 

This happened not to long after messing with the USB start up disk creater and Ubuntu Netbook Remix edition. 

Any ideas? Im clueless

---

### Post by taurus on 2009-07-05
Plug it back in and make sure it's mounted first.  Then, post the outputs of these commands from a terminal.

```
sudo fdisk -l
df -h
```
Perhaps you need to reformat it to remove whatever left behind since the last time you played around with it.

---

### Post by Vrekk on 2009-07-05
Thanks for the Replay, but one of my good friends came over and we got it all sorted out.  He did most of the work so im not sure exactlly what the problem was but it sounded like it was partioned into two parts, one that had one of the OS's on it and the other that was for use as a flash drive. 

We were able to create a new pation table on it with gparted and create one large fat32 partion.  Nows it running as it should. Thanks for the help!

---

