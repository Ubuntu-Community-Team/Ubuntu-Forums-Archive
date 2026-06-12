---
title: "will installing ubuntu erase my entire hard disk ?"
date: 2009-05-17
forum: Installation &amp; Upgrades
---

### Post by andrei C on 2009-05-17
Hello!
I wanted to install Xubuntu on an older computer on which I have Windows.So i read the Installation Guide on the Ubuntu website and I got a little alarmed.It seems that anything I do, I must reformat the entire hard disk, not just one partition.
I have 3 partitions, C (NTFS), D(NTFS), E(FAT32).And, of course, I only want to reformat the C partion, maibe the D one too, because I know that Linux can't read NTFS, only FAT32, but even so, I want to keep my E partition intact, as in not format it and loose all the data.That's my biggest partition and I don't want to loose it.
I don't want to use windows anymore, so I won't need a dual system instalation.I just want to replace Windows whit Xubuntu.That's all.
So, is there any chance to install Xubuntu without having to reformat the entire disk?

Please remenber, that even if this question seems stupid, I tried as much as I could to do some research, both with the installation guide and by searching on google.But this is exactly it, all my research points out to the fact that I must format the entire disk.

---

### Post by cariboo on 2009-05-17
If you are familiar with partitioning hard drives, there is nothing to it. I would suggest you use the manual partition option when you get to the partitoning section during the installation. 

Any linux variant has been able to safely read and write to NTFS partitons for several years, it is vfat that is the problem, there is a 4Gb file size limit, and personally I have quite a few files that are well over 4Gb in size.

---

### Post by Dr. Nick on 2009-05-17
Yes use the manual partitioning option and you can delete the 2 ntfs partitions and create linux file systems, or reformat the ntfs ones in a linux filesystem and leave them the same size. That will allow you to keep the fat32 one intact

---

### Post by albinootje on 2009-05-17
> **andrei C said:**
> 
So, is there any chance to install Xubuntu without having to reformat the entire disk?
As others already pointed out you can choose "manual" partitioning during the partitioning step of the Ubuntu installation.

You should also realise that C: D: and E: are named completely different in Linux.
To be sure, you can choose "Try without making changes" from the Ubuntu installation cdrom, and then start a terminal, and post the output of this command here :
```

sudo fdisk -l

```
Then we can give you further advice how to proceed.

---

### Post by andrei C on 2009-05-17
Thanks everyone!That was some fast response!
Ok, I was going to test Xubuntu anyway, to see if it's compatible with my hardware.And I know that in Linux drives are hda, hdb, hdc, etc. instead of A,B,C.
I will try to be carefull :)

---

### Post by albinootje on 2009-05-17
> **andrei C said:**
> 
Ok, I was going to test Xubuntu anyway, to see if it's compatible with my hardware.

Good idea.
> 
And I know that in Linux drives are hda, hdb, hdc, etc. instead of A,B,C.
I will try to be carefull :)
Okay :)
/dev/hda is from somewhat older kernels. /dev/sda is in use for IDE drives in newer kernels.
No idea when that exactly started, but Ubuntu Hardy already uses it.

This can sometimes be confusing with usb (and scsi) drives or sticks, which already used /dev/sdX in the past.

---

### Post by presence1960 on 2009-05-17
How to partition: [https://help.ubuntu.com/community/HowtoPartition](https://help.ubuntu.com/community/HowtoPartition)

I would suggest reading this.

---

