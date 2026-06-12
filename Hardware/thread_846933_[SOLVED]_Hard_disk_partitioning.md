---
title: "[SOLVED] Hard disk partitioning"
date: 2008-07-02
forum: Hardware
---

### Post by Akash Singhal on 2008-07-02
I have a laptop and I have vista and ubuntu in that (both in separate partitions)..
I installed ubuntu by shrinking the c: drive which contains windows Vista...there are no more partitions in my hard disk viz, Recovery and MediaDirect(Dell)...Now I want to create a partition with FAT32 system so that I can share documents between vista and ubuntu..but I am unable to do so from vista as it says that the disk has reached maximum number of partitions...can it be done in ubuntu. If yes , then how?

Thanks in advance.

---

### Post by pablopancho on 2008-07-02
Hi,

On every disk there can be up to 4 primary partitions. But you can instead create 3 primary partitions and one extended partition. The extended partition can contain many logical volumes, which basically behave just like partitions.

All you need is to do is to delete one primary partition (backup contents first!!!) and create an extended partition in its place. Inside it you can create logical volumes. I am not sure if I'm right but I think the extended partition should be the last partition.

You can do it under vista or you can use linux program called Gparted. There are also other programs but I always use this one.

Be careful when messing with your partitions, [COLOR="Red"]make backups[/COLOR]! 

I'm not an expert but so far this worked for me, so I hope this will help you.

---

### Post by Akash Singhal on 2008-07-02
Will I be able to share data between the logical volumes of the extended partition and windows vista which is in a primary partition???

---

### Post by aquavitae on 2008-07-02
I don't know what file system Vista uses, but if its still NTFS you don't need a fat partition, the ntfs-3g linux driver fully supports reading and writing to ntfs partitions. If you do need a separate partition, I'd suggest using NTFS on it anyway instead of FAT32 - I find FAT32 has far to many limitations (e.g. you can't have a partition larger that about 32Gb).

In answer to your question: It makes no difference to windows or linux whether its a logical partition or a primary partition, so yes, it can share data across them.

---

### Post by Akash Singhal on 2008-07-02
Vista has NTFS system.
I can access the Recovery partition through ubuntu which has NTFS file system but not the C: which contains windows although it also has the NTFS system.
What is linux-3g driver..does that come along with the ubuntu 8.04 or do I need to install it through sudo???

---

### Post by aquavitae on 2008-07-02
The ntfs-3g driver comes pre-installed in 8.04, so you should be able to access the windows C drive.  What exactly happens when you try - or don't you get the option to? You can try to mount it manually with ```
gnome-mount /dev/sda1
```assuming the c drive is on the partition /dev/sda1.

---

### Post by Akash Singhal on 2008-07-02
I dont even get the option...
It shows me just MediaDirect and Recovery Partition.
thanks for ur help..I'll try the command.

---

### Post by aquavitae on 2008-07-02
Chances are it the command I gave work if you don't get the option to do it from the gui. If it doesn't then try these command:
```
sudo mkdir /media/windows_c
sudo mount /dev/sda1 /media/windows_c
```
Once again, making sure /dev/sda1 is correct.

---

### Post by Akash Singhal on 2008-07-02
yippeee

gnome-mount /dev/sda1 worked for me....thanks a lot for you...

---

### Post by aquavitae on 2008-07-02
Great. It should show in Places every time you start up, but it might have an unexpected name - e.g. disk. This is because it names it by volume label rther than where it is or whats on it. If you have any more problems post back.

---

### Post by Akash Singhal on 2008-07-02
yeah...it is named as OS.
Sure, I will contact you in case of any problem.

---

