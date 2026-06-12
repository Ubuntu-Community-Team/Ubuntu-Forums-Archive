---
title: "mounting cd drive"
date: 2014-09-05
forum: Hardware
---

### Post by bm143 on 2014-09-05
I have a question on  mounting and no matter how hard I try I cannot get it and I am getting  very frustrated all i want is to be able to use my CD-ROM that’s all. so  let me give you some info about my computer i used to have ubuntu 12  and upgraded to ubuntu 14 and did the update now my system is up to date  I cannot get the cdrom to work.so in my root folder i have a folder  called cdrom. in my root folder i have a folder called media and in that  i have a folder called cdrom and in my dev folder i have a file called  cdrom and i dont know if fstab document has anything to do with this but  i see people posting the contents of their fastab document which is in  etc to try to figure out what is going on so i dont know if that helps  or not but i will put the contents of that document here ..........
  [h=1]/etc/fstab: static file system information.[/h]  #
  [h=1]Use 'blkid' to print the universally unique identifier for a[/h]  [h=1]device; this may be used with UUID= as a more robust way to name devices[/h]  [h=1]that works even if disks are added and removed. See fstab(5).[/h]  #
  [h=1][/h]  [h=1]/ was on /dev/sda1 during installation[/h]  UUID=1a2a862b-d1d1-4d98-b172-62ad4f3bb826 /               ext4    errors=remount-ro 0       1
  [h=1]swap was on /dev/sda5 during installation[/h]  UUID=b6c59812-f866-4171-9025-334af75dacd8 none            swap    sw              0       0
  ...................Read 11 lines (Warning: No write permission)
  that is what my fstab looks like also i dont know if this helps but  on a website this command is supposed to tell you if your cdrom what  type it is or something the command was lsblk and this is the result of  that command.....
  NAME     MAJ:MIN    RM     SIZE    RO    TYPE     MOUNTPOINT sda      8:0         0     141.1G  0     disk --sda1   8:1         0     146.6G  0     part     / --sda2   8:2         0     1K      0     part --sda5   8:5         0     2.5G    0     part     [SWAP] sr0     11:0         1     276.4M  0     rom
  thats pretty much all the info i have my cd drive is actually a dvd  rw drive my computer is an old e-machines still runs great on linux all i  need is to get my darn cd-drive to work i hope i have supplied enough  info to get this figured out
  also i know about the mount /dev/cdrom /mnt/cdrom  but this dont work  i get an error and theres that other one with 9660 or sonething that  dont work either i dont know what to do please help me thank you

---

### Post by yancek on 2014-09-05
Does this happen with any CD regardless of what type of data is on it?  You don't post the command you use to try to mount so it's difficult for anyone to correct it.  The command you posted shows your cdrom is /dev/ sr0.  When you put a CD in the drive and go to /media/cdrom, does anything show?  If not use the command below to try it:

```
sudo mount /dev/sr0 /media/cdrom
```

Your post is poorly written with long run-on sentences and no punctuation whatsoever which makes it very difficult to read and probably causes people to take a look and just move on.  Try to do better next time.

---

