---
title: "partition advice for new laptop"
date: 2009-09-18
forum: Installation &amp; Upgrades
---

### Post by dix0r on 2009-09-18
hey all, 

just bought a dell studio 1555, tried to dual boot between vista and ubuntu, then decided to re-install ubuntu and nix vista. 

i'd like to reinstall one more time and properly manually partition my disk (500 gb)

i don't have anything on the drive yet worth salvaging. 

my understanding is that a good way to do it would be to create:


[LIST]
[*]primary (ext3) of 10-20 GB for /
[/LIST]

[LIST]
[*]logical/extended for the rest
[*]create a swap within the extended of about 8 gb (double my 4 gb ram)
[/LIST]
now, how should i split up the remainder between home and data? 

also, should all partitions be ext3?

many thanks!

---

### Post by imhotep59 on 2009-09-18
How to split the remainder depends on what you need and what you want. I suggest you make a DATA partition in NTFS to store documents that you wish to share between Ubuntu and Vista (Ubuntu can read NTFS partitions). Then you will need an ext partition (/home) to store documents that will be exclusively accessed with Ubuntu (Vista cannot read ext or it will require a specific program). So, choose the respective sizes of these 2 partitions in accordance to your documents and files for Vista and Ubuntu.
If you use Ubuntu 9.04, you can format / and /home in ext4 (the most recent format which is now stable and will be the default format in Karmic Koala)

---

