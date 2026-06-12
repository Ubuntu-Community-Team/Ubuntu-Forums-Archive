---
title: "Installation help needed for dual boot laptop"
date: 2009-06-06
forum: Installation &amp; Upgrades
---

### Post by ro7 on 2009-06-06
I would like to install Ubuntu 9.0.4 on a DellVostro 1500 (Core2Duo, 2Gb ram, 320 Gb HD Intel graphics X3100, Dell wireless 1395, HD Audio 2). The LiveCD seems to work, I am able to play music and edit photos but have not looked at networking. The HD has 4 partitions, NTFS 17Gb for Windows XP, 17Gb unformmatted (for Linux) and two 133Gb NTFS data partitions. I realize that it is recommended to install Linux into 3 or 4 partitions but for my initial try I would like to just use one Linux partition and keep WinXP. I guess I could make 2 additional extended partitions but would prefer to go with the easiest method. I am reasonably familiar with XP. 

I tried installing but do not know how to respond to the partition editor prompts, 
UseAs: Ext3, Ext4, Ext2, Reiser, JFS, XFS, Fat16, Fat32, swap  --> Ext3 ??
Format:  --> Yes
MountPoint: /, /boot, /home, /temp, usr, ...                   --> ??

Unfortunately this is the first time posting on a forum/blog also so I do not know any of the rules/procedures.

---

### Post by vodnguyen on 2009-06-06
@ro7: I just explain to you this.
- Ext3, Ext4, Ext2, Reiser, JFS, XFS, Fat16, Fat32, swap : are some kind of hard disk formats. My advice is Ext3 and a partition for swap (recommend its capacity = 1.5 RAM capacity).
- Mount point : you will point ubuntu to save your file system in that partition !! My advice is : mount it as /.

Hope this useful for you.

---

