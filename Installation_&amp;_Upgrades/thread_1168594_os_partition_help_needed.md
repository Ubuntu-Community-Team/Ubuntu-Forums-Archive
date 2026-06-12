---
title: "os partition help needed"
date: 2009-05-24
forum: Installation &amp; Upgrades
---

### Post by salim.madni on 2009-05-24
dear gurus

i do have 146GB disk, where i need 2 create the partitions

/ swap
/ root and all related to os matters here
/ extra partition for applications,antivirus,software

but i am not getting sucess

can some one advise on this, how to assess max size of os

regards
salim

---

### Post by whoop on 2009-05-24
> **salim.madni said:**
> dear gurus

i do have 146GB disk, where i need 2 create the partitions

/ swap
/ root and all related to os matters here
/ extra partition for applications,antivirus,software

but i am not getting sucess

can some one advise on this, how to assess max size of os

regards
salim
You usually don't make an extra partition for applications (unless it is some kind of backup/storage), you could create a separate home partition which stores all you user related files-->configuration, documents, pictures, videos etc.
So you could just stick with:
root and swap
or more flexible
root and home and swap
or even more flexible
boot and root and home and swap

If choose to install ubuntu you can configure your partitions during the setup process. If you want to do that outside of the installation process you can start a livecd and in the terminal type:
```

gksudo gparted

```
This will launch a partition editor.

---

### Post by x33a on 2009-05-24
go like this

1. 15 GB for / (root) as ext3 or ext4 (your choice).
2. 2 times your ram for swap.
3. format the rest as ext3 for storage. no need to set a mount point for this partition here.

---

### Post by salim.madni on 2009-05-24
dear gurus

advise further

1) root should be primary partition? make as / right
2)2gb physical memory, so make it 4gb,  swap should be primary partition?
3) for application rest everything go inside, it should be primary or logical

any effect on system performance stability reliability of use logical

regards

---

### Post by x33a on 2009-05-24
you can have a max of 4 primary partitions and since you intend to make only 3, then you should go with primary partitions.

there is no effect on performance using a logical partition though.

as for 4GB swap, only set it if you intend to hibernate, else with 2GB ram you'll rarely use the swap.

---

### Post by doomsword2001 on 2009-05-24
hello

1) i have 5gb swap on 3gb ram pc, doesnt seem to be used. i think its a waste of hard disk. 
2) all ur programs should be installed on / , so no additional space and 10-20gb for / should be ok.
3) /home is where u store mp3 movies etc

so it depends on you, if u want lots of programs give more space to /
if u need to download mp3s and staff and do not have an external disk give more space to /home

---

