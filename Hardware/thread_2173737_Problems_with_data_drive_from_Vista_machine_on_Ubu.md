---
title: "Problems with data drive from Vista machine on Ubuntu"
date: 2013-09-11
forum: Hardware
---

### Post by rob20 on 2013-09-11
Hi everyone.

My Windows Vista machine died on me. Since then I  have started using Ubuntu on a different machine. Last night I removed  my data drive from my Vista box and plugged it into the Ubuntu box.   Unfortunatley I seem to be missing loads of files.  In one directory I  should have hundreds of sub directories and files but I only see one  directory.

The drive is a Segate 2TB Model ST2000DL003
I have an XP box that reports the drive to contain a GPT protected partion.

I do not have the space to back the drive up or the cash to buy a new drive.

Does  anyone have any advice on how to recovery the data on the drive or  check what is left of the data. I know very little about partions and  the tools used to test them and don't wish to start writing data to the  drive without some idea of what I'm doing.

Any advice would be much appreciated. 

Thanks

Rob.

---

### Post by carl4926 on 2013-09-11
In ubuntu with the drive in question attached
Post the result of

```
sudo parted -l
```

---

### Post by rob20 on 2013-09-11
Hi carl4926

Output from sudo parted -l as follows :-

```
Model: ATA ST2000DL003-9VT1 (scsi)
Disk /dev/sda: 2000GB
Sector size (logical/physical): 512B/4096B
Partition Table: gpt

Number  Start   End     Size    File system  Name  Flags
 1      1049kB  2000GB  2000GB  ntfs


Model: ATA Maxtor 6Y120M0 (scsi)
Disk /dev/sdb: 123GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End    Size    Type      File system     Flags
 1      1049kB  122GB  122GB   primary   ext4            boot
 2      122GB   123GB  1072MB  extended
 5      122GB   123GB  1072MB  logical   linux-swap(v1)
```

Thanks

---

### Post by carl4926 on 2013-09-11
It looks normal
Do you have another windows machine that could check the drive for errors?

BTW what version of Ubuntu are you using?

---

### Post by rob20 on 2013-09-11
Currently I have one working machine. This has Ubuntu 13.04 on it.  I also have two other drives in the machine. One is the problem drive. The other is a windows XP drive. (The XP drive is currently unconnected as I do not have dual boot/any boot manager installed. I have to power down and switch drives to boot xp :-{ )

---

### Post by carl4926 on 2013-09-11
> **rob20 said:**
> Currently I have one working machine. This has Ubuntu 13.04 on it.  I also have two other drives in the machine. One is the problem drive. The other is a windows XP drive. (The XP drive is currently unconnected as I do not have dual boot/any boot manager installed. I have to power down and switch drives to boot xp :-{ )
Then I'd try that.

Technically you should be able to connect the XP drive and update grub to get dual boot, but lets not complicate matters.

---

### Post by rob20 on 2013-09-11
I don't have enough free sata power connectors to get all three drives running at the same time so dual boot is only an option if I remove the data drive.  I am curently rather under resourced.

I'll switch to XP now and give the disk check a go.  I'll be back when its done.

Thanks for your help so far.

Rob.

---

### Post by rob20 on 2013-09-11
Windows disk Manager reports Health (GPT Protective Partition) with no drive letter. When I right click on the drive everything except help is greyed out so I am unable to assign it a drive letter and thus can do nothing with it.

I had a quick search on the net and found this :-
> GPT only works on Windows 7/8/Vista/2008 and 64-bit version of Windows  XP/2003, but 32-bit version of Windows XP/2003 are not acceptable from [here]("http://ubuntuforums.org/www.disk-partition.com/blog/how-to-access-gpt-protective-hard-disk-on-windows-xp/"), and of course I'm on xp 32 bit.

Unfortunately I do not have access to a version of windows above XP at the moment.
I do have a sata usb drive caddy and my next door neighbor has a higher version of windows so I might see if I can pinch his machine for a few hours.

Other than that I'm currently ubuntu only unless there is a live cd that could be of some help somewhere....

---

### Post by carl4926 on 2013-09-11
I don't know enough about the windows stuff.
Gparted has a check option > right click the partition > check (from the context menu), it's not as comprehensive as windows tools though

---

### Post by carl4926 on 2013-09-11
And check this
[http://ubuntuforums.org/showthread.php?t=1907603&p=11604167#post11604167](http://ubuntuforums.org/showthread.php?t=1907603&p=11604167#post11604167)

---

### Post by rob20 on 2013-09-11
Just fired up Gparted and noticed a red '!' icon. Checking the information on the drive gives the window below :

[IMG]http://i.imgur.com/DY6G2Ph.png[/IMG]
so I think we may be getting somewhere. Trying the disk check option fails with errors similar to the above so I guess I'll need a copy of windows. I'll try and pinch my neighbors machine and run a disk check with that.

Thankyou so much for your help. I was worried i'd end up writing to the disk and wiping my data.

Think I have a method to at least check the drive now if not repair it.

Thanks

Rob

---

### Post by carl4926 on 2013-09-11
Good luck

---

### Post by rob20 on 2013-09-11
Thanks.  Think I'll stick Lilo or grub on this box as well and sort out dual boot.  Should make life a little less tedious.

Thanks for your advice.

Rob

---

### Post by Mark Phelps on 2013-09-11
According to Google > GPT hard disk is one kind of disk style. In computer hardware, GPT is a standard for the layout of partition table on a physical hard drive. It breaks up the limitation of four primary partitions, and it supports the number of partitions up to 128 per disk. However, 32-bit version of Windows XP will see only the Protective MBR and the EE partition will not be mounted

So basically, you can't use GPT with XP.

---

