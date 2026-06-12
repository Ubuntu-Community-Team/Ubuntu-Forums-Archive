---
title: "automatic install with preseed file"
date: 2009-07-24
forum: Installation &amp; Upgrades
---

### Post by krishantha on 2009-07-24
Hi
 i setup the remote installation server to insatll ubuntu 180 notebook PC s. it is work well. I have some concerns as follows.

01.
I setup it with  preseed file. if I use partition type as 
[COLOR=Blue]"d-i partman-auto/method string regular"[/COLOR]
it work without user involment. but if i use 
[COLOR=Blue]d-i partman-auto/method string lvm[/COLOR]
then it ask for LVM size. how do i pass through file.

and also how can i create cistome file structure such as
/boot 100MB ext2
/swap 3GB
/        30FB ext3

remain on LVM
/u01 ext3

[SIZE=3][COLOR=DarkRed]does any one have working preseed file ??? if so please send it.[/COLOR][/SIZE]

---

