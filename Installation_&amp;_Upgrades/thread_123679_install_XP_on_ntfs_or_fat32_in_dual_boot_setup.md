---
title: "install XP on ntfs or fat32 in dual boot setup?"
date: 2006-01-30
forum: Installation &amp; Upgrades
---

### Post by asinsh on 2006-01-30
I am doing a brand new dual boot install of windows XP and ubuntu on a single harddrive, and I've done enough reading to realize that files that both operating systems need to read and write to should be placed in a FAT32 partition.

It would be simpler (fewer partitions and less alphabet soup on drive letters) to install XP in a single large FAT32 partition (maybe 200GB out of the 300GB on my drive) rather than installing XP in an ntfs partition and creating a separate partition that both o/s would share.  Is that the way to go, or will I be losing anything important by not installing XP on an ntfs partition?

---

### Post by philipgm on 2006-01-30
I think that XP installs onto FAT32 by default and then you can choose to change to NTFS. NTFS is supposed to be a superior file system, but I've never noticed any real difference in terms of day to day use. 

I'm not sure about support for writing NTFS partitions in Linux so you might be better off with FAT32 if you want to write to your windows partition from Linux.

Phil

---

### Post by kenweill on 2006-01-30
[QUOTE=philipgm]I think that XP installs onto FAT32 by default and then you can choose to change to NTFS. NTFS is supposed to be a superior file system, but I've never noticed any real difference in terms of day to day use. 

I'm not sure about support for writing NTFS partitions in Linux so you might be better off with FAT32 if you want to write to your windows partition from Linux.

Phil[/QUOTE]

FAT32 has slow performance especially on large capacity drives. And FAT32 has limitations when it comes to capacity. Just like FAT(FAT16) which is limited only to 2Gig. I forgot the capacity limit of FAT32.

NTFS performance do not change whether its small capacity drives or large capacity drives.

---

### Post by asinsh on 2006-01-30
[QUOTE=philipgm]...I'm not sure about support for writing NTFS partitions in Linux so you might be better off with FAT32 if you want to write to your windows partition from Linux....[/QUOTE]
Right, as I understand it, my chocies are:

- install XP in an ntfs partition and put any files I need to share between the operating systems in a separate FAT32 partion (which means more alphabet soup on drivenames)

or

- install XP on one big FAT32 partition and forego whatever benefit there is of installing it on an NTFS partition.

Which is more sensible, assuming I have no desire to compress or encrypt my files?

---

### Post by GTvulse on 2006-01-30
[QUOTE=asinsh]I am doing a brand new dual boot install of windows XP and ubuntu on a single harddrive, and I've done enough reading to realize that files that both operating systems need to read and write to should be placed in a FAT32 partition.

It would be simpler (fewer partitions and less alphabet soup on drive letters) to install XP in a single large FAT32 partition (maybe 200GB out of the 300GB on my drive) rather than installing XP in an ntfs partition and creating a separate partition that both o/s would share.  Is that the way to go, or will I be losing anything important by not installing XP on an ntfs partition?[/QUOTE]
XP installs on NTFS by default, but you can choose to use FAT32 if you go to the partitioner during installation.

You will lose file access features, which, IMO, help restricting viral invasion when combined with restricted use of administration rights in the day-to-day use acconts. Yet, you can be safe (as far as safe is safe) if you have a security discipline and policy, including a good antivirus (I suggest [avast]("http://www.avast.com/"), free for home use), malware detection software, and other tools to keep your registry clean and sane. The firewall that comes with XPSP2 is OK. It is a lie that you need an IDS integrated with a firewall, unless you are so mindless as to push the virii yourself (that is using Internet Explorer with execution rights open to any ActiveX a run-of-the-mill pr0n or warez site may oblige... ;-)).

EDIT: kenweill is correct. FAT32 start degrading performance if the drive is bigger than 32 Gb. You can create quite big FAT32 filesystems if you want (I've seen 400 Gb filesystems) but fragmentation is a killer.

---

### Post by asinsh on 2006-01-30
[QUOTE=kenweill]...NTFS performance do not change whether its small capacity drives or large capacity drives.[/QUOTE]
So it sounds like you would suggest sticking XP on an NTFS partition and only using a FAT32 partition for files that both XP and ubuntu need read and write access to, correct?

---

### Post by ddtmsa on 2006-01-30
I installed Ubuntu on an XP computer with an NTFS filesystem following exactly the faq from

[http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)

For what it is worth on an 80GB hard-drive, I kept a 64GB NTFS partition, created a 4GB FAT32 partition which both XP and Ubuntu can read/write to, and a 12GB Ubuntu only partition. 

If you haven't looked at the above hermanzone site, I can highly recommend it for its step by step instructions on dual-booting.

---

### Post by kenweill on 2006-01-30
[QUOTE=asinsh]So it sounds like you would suggest sticking XP on an NTFS partition and only using a FAT32 partition for files that both XP and ubuntu need read and write access to, correct?[/QUOTE]

No. Not really.
By the way, are you in a network?
Why do you want a dual-boot?

Me, i'm on a network.
I don't use a dual boot. I installed Windows XP inside my Ubuntu Linux using VMware Player.
Format Windows XP as NTFS. Create a shared folder. And through the network, I can access the files in the shared folder of WinXP from Linux.

The only problem I have is accessing my files in Linux from Windows. Don't know how to setup SAMBA. I can't make it work.

---

