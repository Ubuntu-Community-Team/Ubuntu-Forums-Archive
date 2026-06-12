---
title: "Unable to mount specific NTFS partition in live mode"
date: 2018-11-02
forum: Hardware
---

### Post by thecosmos on 2018-11-02
Few days back I dropped my laptop damaging screen and probably its hard drive. I made bootable Ubuntu 18.0 LTS USB and managed to boot into its live mode using my external monitor through HDMI. 
Ubuntu installation menu doesn't detects my hard drive but I am able to see my partitions of hard drive from files > other locations. I am able to mount and view files of 2 of my partitions ( C Drive where windows was installed and E) but i don't know why when I am trying to open my D drive partition, files app crashes and I get an internal error.
How do I mount that partition or install ubuntu as my primary OS on C drive.

---

### Post by yancek on 2018-11-02
If the computer/drive is physically damaged there won't be anything anyone can do with software.  How are you trying to access your "D" drive?  Are you doing it through a file manager/GUI?  Have you tried manually mounting it from a terminal?  First step would be to create a mount point for your "D" drive then issue the mount command.  You would need to know which partition your "D" drive is which you should be able to ascertain with the fdisk -l command based on the size of the partition.  Linux doesn't use the windows naming conventions with letters for drives which is a carryover from the 1970's so you will need to familiarize yourself with that or post the output of fdisk here.

```
sudo fdisk -l
``` Lower case Letter L in the command
```
sudo mkdir /mnt/Ddrive
```
```
sudo mount /dev/???? /mnt/Ddrive
```

You can change "Ddrive" to something else that is meaningful to you, that is just an example.  Where you see ???? is where you would put the partition number for what is your "D" drive.  If you don't know that, post the fdisk output here and someone should be able to help.

> How do I mount that partition or install ubuntu as my primary OS on C drive. 

You can't install Ubuntu or any Linux on your "C" drive as it has an ntfs filesystem.  YOu would need to shrink the windows partitions to create unallocated space on the drive on which to install Ubuntu or you could simply install Ubuntu with the ERase disk option.  If you do select this option, it WILL overwrite everything on the computer so backup or move any personal data you want BEFORE doing this.

---

### Post by Mark Phelps on 2018-11-03
@thecosmos:

You are mentioning "C" and "D" drives -- so I have to presume that you are trying to recover files/folders from a Windows system, right?

Problem is if this PC was running Win10, then a new hybrid sleep/hibernation feature known as Fast Startup was AUTOMATICALLY enabled and that will prevent you from accessing the drives from Linux as they remain MOUNTED even though Windows is no longer running.

You might be able to FORCE a mount in Linux, but then you risk corrupting the partitions in the process.

---

