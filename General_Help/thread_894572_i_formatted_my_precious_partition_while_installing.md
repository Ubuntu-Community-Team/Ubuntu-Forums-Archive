---
title: "i formatted my precious partition while installing ubuntu"
date: 2008-08-19
forum: General Help
---

### Post by xnostradamusx on 2008-08-19
a little help here pls my problem is what the topic title is all about,

im asking if anyone knows how to solve this because in windows xp i have 

used a program that can recover deleted/formatted files or partitions

but i dont have any idea on what to do here in ubuntu.

hoping someone can help me out here

---

### Post by fahadsadah on 2008-08-19
What file system was the partition (ntfs, ext3, fat32, hfs+, etc)

---

### Post by az on 2008-08-19
[https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)

You will need another drive onto which you will put the recovered files.  You need to data-carve them out, since the filesystem is no longer there.
[https://help.ubuntu.com/community/DataRecovery#Extract%20individual%20files%20from%20recovered%20image](https://help.ubuntu.com/community/DataRecovery#Extract%20individual%20files%20from%20recovered%20image)

---

### Post by xnostradamusx on 2008-08-19
> **fahadsadah said:**
> What file system was the partition (ntfs, ext3, fat32, hfs+, etc)


its a windows partition and its a NTFS all my important files is in there and that partition was deleted\formated and 

installed with this ubuntu im using right now

my important files consists of pictures\iso's\cso's

---

### Post by fahadsadah on 2008-08-19
It would be best to use a Windows based utility. Turn off your computer by the plug, remove the disk and insert it into an ALREADY RUNNING Windows machine, from where you can run an unformat program. DO NOT TURN ON / OFF THE COMPUTER WITH THE DISK IN IT (turnoff by power is allright)

---

### Post by xnostradamusx on 2008-08-19
> **fahadsadah said:**
> It would be best to use a Windows based utility. Turn off your computer by the plug, remove the disk and insert it into an ALREADY RUNNING Windows machine, from where you can run an unformat program. DO NOT TURN ON / OFF THE COMPUTER WITH THE DISK IN IT (turnoff by power is allright)


i hope i can do that but im using a laptop with 120gb hdd partitioned in 

half and i deleted\formated\ installed ubuntu where my important files 

resides so removing my hdd is not an option i think

---

### Post by wirelessmonkey on 2008-08-19
Hotswapping can fry your disk controller, beware that suggestion.

---

