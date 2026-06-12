---
title: "Sick of my SATA disk, please help"
date: 2008-11-19
forum: General Help
---

### Post by Green_Star on 2008-11-19
hi,

I am user of Ubuntu since two years. A year ago I bought a new SATA disk. It used to work fine but if I try to copy or paste any big file(like more than 400mb) my system used to hang, otherwise I am fine with doing stuff like saving documents, pictures, music etc. that time I figured out that there are no good support for SATA in Linux world. 

This problem was almost gone when I moved to 804, everything is working fine and from a month onwards my system again starting handing. Surprisingly it is not like before, now when ever I access the disk it is hanging, I didnt even open a file, i just clicked on disk, it shows the content and in 3-4 secs my whole system hangs. none works, like Ctrl+Alt+F1 or Ctrl+Alt+Backspace etc. I had to manually hard reboot, that sucks. 

I opened my case and reattached the disk to make sure any loose connections, and testing in winxp, everything is fine. But same thing happens in Ubuntu, I tried in 810, same thing. I reinstalled 804 same thing. No logs found about this, looks like complete system is hanged. 

Is there any other way to know the problem? like any partition corrupt or bad file system etc. can I run fsck without mounting the drive? any graphical disk check utility? 

thanks in advance.

---

### Post by Bluebell392 on 2008-11-19
Have you tried running fsck from a live cd?

---

### Post by Green_Star on 2008-11-19
Thank you for replying me. 

Thats the thing I thought just before I am posting this. I will try this after going home. Do I need to mount the drive before doing fsck? 

I never ran fsck, I will look into its syntax, but anyway could you suggest fsck syntax? 

Thanks.

---

### Post by taurus on 2008-11-19
You should not mount the drive/partition first if you plan to run fsck.

```
man fsck
```
Is it ntfs or ext3 filesystem?  I assume it's ntfs since you said you tested it in windows and the drive appears to be fine.

If it's ntfs, you can just forget about the fsck then.  Instead, boot into windows and run defrag and disk scan on that drive then.

---

### Post by Green_Star on 2008-11-19
Thank you, 

this disk has three partitions, two in ext3 and one in ntfs. I do access these two ext3 partitions in windows using some program(I do not remember it now, something like IFS drive?).

> **taurus said:**
> You should not mount the drive/partition first if you plan to run fsck.

```
man fsck
```
Is it ntfs or ext3 filesystem?  I assume it's ntfs since you said you tested it in windows and the drive appears to be fine.

If it's ntfs, you can just forget about the fsck then.  Instead, boot into windows and run defrag and disk scan on that drive then.

---

### Post by dabl on 2008-11-19
> **Green_Star said:**
> Thank you, 

this disk has three partitions, two in ext3 and one in ntfs. 


That doesn't sound right.  If there are only three partitions, I would have expected to read "one ext3, one swap, and one NTFS".  This leads to some questions:

1. Do you have a swap partition?

2. Is this troublesome SATA drive the only hard drive in the computer?

3. In your BIOS, for the SATA bus there should be a "mode" setting that you can change.  If it is set to "auto", try "RAID" or "AHCI" or "Legacy IDE" if you have those choices.

---

### Post by Green_Star on 2008-11-19
I have three drives, first two are normal PATA and third one is SATA. My machine boots from one of the PATA, and it got swap partition 

I am not sure about BIOS settings. I will check the BIOS options one more time, I believe I setup it as auto.

I do not have RAID setup, so why do I have to try with RAID? 

> **dabl said:**
> That doesn't sound right.  If there are only three partitions, I would have expected to read "one ext3, one swap, and one NTFS".  This leads to some questions:

1. Do you have a swap partition?

2. Is this troublesome SATA drive the only hard drive in the computer?

3. In your BIOS, for the SATA bus there should be a "mode" setting that you can change.  If it is set to "auto", try "RAID" or "AHCI" or "Legacy IDE" if you have those choices.

---

### Post by taurus on 2008-11-19
You can run fsck on the two ext3 partitions but you need to get into windows to run defrag and scandisk for the ntfs partition.

As long as you don't mount those two partitions in Ubuntu, you can run fsck without using the LiveCD.

---

### Post by Green_Star on 2008-11-19
Thank you.

I will scan two ext3 drives from ubuntu, as I do not access ntfs drive from Ubuntu I do not have to worry abt it for now. 

The surprising thing is, I can access one of those trouble two ext3 drives in Ubuntu for around 2-4 sec, I can do anything in that short time like browsing folders, subfolders or quick open a file etc. Once I pass that time the system will be freeze...hahahah.

---

### Post by dabl on 2008-11-19
> **Green_Star said:**
> I have three drives, first two are 

I do not have RAID setup, so why do I have to try with RAID?



Check this:

[http://en.wikipedia.org/wiki/Advanced_Host_Controller_Interface](http://en.wikipedia.org/wiki/Advanced_Host_Controller_Interface)


If you post your /etc/fstab file, it might reveal something too.

---

### Post by psusi on 2008-11-19
> **Green_Star said:**
> that time I figured out that there are no good support for SATA in Linux world. 


That's not true.  Linux has had SATA support for quite some time.  I've been running Ubuntu on a raid of two sata 10,000 rpm 36 gig WD Raptors since breezy.

It sounds like your motherboard has a bug.  You might try booting with the nomsi option and see if that helps.  Press e when grub is coming up to edit the boot commands, and add the word "nomsi" to the end of the kernel line.

What kind of cpu and how much ram do you have?

---

### Post by Green_Star on 2008-11-19
> **dabl said:**
> Check this:

[http://en.wikipedia.org/wiki/Advanced_Host_Controller_Interface](http://en.wikipedia.org/wiki/Advanced_Host_Controller_Interface)


If you post your /etc/fstab file, it might reveal something too.

I was doubted about that, and removed the lines belongs those drives and tried to connect manually thru nautilus(by clicking on the drive at left side panel). Still I got same thing.

Any way as I re-installed ubuntu 804, nothing can be found in fstab. And when I connect(temporary, I think nautilus uses pmount for this)  manually thru nautilus still same thing.

---

### Post by dabl on 2008-11-19
The Ubuntu installer will not automatically find and mount hard drives and non-system partitions.  So you're not going to open Nautilus, as a user, and do anything until those drives/partitions are mounted.  :(

---

### Post by taurus on 2008-11-19
> **Green_Star said:**
> I was doubted about that, and removed the lines belongs those drives and tried to connect manually thru nautilus(by clicking on the drive at left side panel). Still I got same thing.

Any way as I re-installed ubuntu 804, nothing can be found in fstab. And when I connect(temporary, I think nautilus uses pmount for this)  manually thru nautilus still same thing.

So you want to mount those three partitions (2 ext3 & 1 ntfs)?  Post the outputs of these commands from a terminal.

```
sudo fdisk -l
sudo blkid
cat /etc/fstab
mount
```

---

### Post by Green_Star on 2008-11-19
> **psusi said:**
> That's not true.  Linux has had SATA support for quite some time.  I've been running Ubuntu on a raid of two sata 10,000 rpm 36 gig WD Raptors since breezy.

It sounds like your motherboard has a bug.  You might try booting with the nomsi option and see if that helps.  Press e when grub is coming up to edit the boot commands, and add the word "nomsi" to the end of the kernel line.

What kind of cpu and how much ram do you have?


I was telling about my beginning days of Ubuntu, there are many threads open with SATA problems, so I though like that. 

I will try with nomis option and see what happens. I do not think there is a bug in mother board, because before I completely move to Ubuntu I used that disk very well in WinXP. And still there is a small partition in ntfs, that works well in WinXP, that proves no hardware problems. 

My system specs
   1. GIGABYTE GA-K8N Pro-SLI 939 NVIDIA nForce4 SLI ATX AMD Motherboard with 1394b
   2. Hauppauge WinTV-PVR 150 MCE FM 1042 PCI Interface
   3. AMD Athlon 64 3700+ San Diego 2.2GHz Socket 939 Single-Core Processor Model ADA3700BNBOX
   4. Total 2GB RAM (CORSAIR 2 x 512MB 184-Pin DDR SDRAM DDR 400 (PC 3200) Dual Channel Kit Desktop Memory Model VS1GBKIT400, 1GB DDR MEMORY PC3200 (400MHz) )
   5. SAPPHIRE 100143L Radeon X1300PRO 256MB 128-bit GDDR2 PCI Express x16 CrossFire Supported Video Card
   6. HDD1 - 40GB(installed with Ubuntu and WinXP) PATA, HDD2 - 250GP (DATA- Dedicated to Ubuntu) PATA, HDD3 - 500GB SATA (has problems)

---

### Post by Green_Star on 2008-11-19
yes, ubuntu by default do not mount any drives except the root file system. Right now I do not have anything in my fstab related to my HDD2 and HDD3. After every fresh boot of my machine I mount the drive by clicking on the drive in nautilus left panel and enter password. 

If you want above commands output, I can do that after around 90min (I am at work, I do that after going home). 

By the way if every thing is good with nomis option, then what do you suggest? How can i make it permanent? I can modify menu.lst but I am not sure whether it carries this option when kernel updates.

---

### Post by Green_Star on 2008-11-19
[http://en.wikipedia.org/wiki/Advanced_Host_Controller_Interface](http://en.wikipedia.org/wiki/Advanced_Host_Controller_Interface)

That is very good information, thank you.

---

### Post by dabl on 2008-11-19
> **Green_Star said:**
> 

After every fresh boot of my machine I mount the drive by clicking on the drive in nautilus left panel and enter password. 



That does not sound like a good way to mount a hard drive -- maybe it's the way to open a USB stick.

I would make mount points (directories) in /media for your drives, and use the "mount" command in the normal way to mount them.  If they mount correctly that way, then I would edit the /etc/fstab file and put a mount line in there to mount them automatically when the system is booted.  :)

---

### Post by KeyserSoze93 on 2008-11-19
Have you got enough power? I had three HDDs (two PATA and a SATA) and my system was hanging one and off when I tried to access drive to I got a better PSU, then is worked (and is still working) fine (including the SATA, so I don't think it's a driver issue)

---

### Post by Green_Star on 2008-11-19
Yes, this is not a good way to mount manually every time. I mounted my second PATA HDD with fstab in /mnt/drive01 and it is working fine. I didn't connect SATA because it has problems. 

I do not think it is problem with enough power. Because it used to work fine before and still works fine in windows. I have 500watt PSU. But still I will try disconnecting unwanted stuff to this this thing like disconnect couple of fans, disconnect one PATA and tv tuner card.

---

### Post by Green_Star on 2008-11-19
> **taurus said:**
> So you want to mount those three partitions (2 ext3 & 1 ntfs)?  Post the outputs of these commands from a terminal.

```
sudo fdisk -l
sudo blkid
cat /etc/fstab
mount
```

here is my output.

> $ sudo fdisk -l


Disk /dev/sda: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x2cc92cc8

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2550    20482843+   7  HPFS/NTFS
/dev/sda2            4623        4865     1951897+  82  Linux swap / Solaris
/dev/sda3            2551        4622    16643340   83  Linux

Partition table entries are not in disk order

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x160baef7

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       30401   244196001   83  Linux

Disk /dev/sdc: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x14ffede8

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1        8534    68545480+   7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sdc2            8535       34667   209913322+  83  Linux
/dev/sdc3           34668       60801   209921355   83  Linux

> $ sudo blkid
/dev/sda1: UUID="2650E22750E1FD85" TYPE="ntfs" 
/dev/sda2: TYPE="swap" UUID="71ef4499-a104-418f-9d76-ed8015a1adb8" 
/dev/sda3: UUID="f294349a-ecd0-49a1-8607-4206d8c732e4" TYPE="ext3" 
/dev/sdb1: UUID="2dddfdcf-54dc-44e0-b20e-be6e2ae1e047" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdc1: UUID="4894716294715382" LABEL="New Volume" TYPE="ntfs" 
/dev/sdc2: UUID="6e0656fa-9878-43ba-9498-01b87e56ea3c" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdc3: UUID="f15138b1-5213-44f4-9486-3eb30f2eef7a" SEC_TYPE="ext2" TYPE="ext3" 


> $ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda3
UUID=f294349a-ecd0-49a1-8607-4206d8c732e4 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda2
UUID=71ef4499-a104-418f-9d76-ed8015a1adb8 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/scd1       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0


# /dev/sdb1 250GB drive
/dev/sdb1 /mnt/disk01 ext3 relatime,defaults 0 2


> $ mount
/dev/sda3 on / type ext3 (rw,relatime,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.24-21-generic/volatile type tmpfs (rw)
/dev/sdb1 on /mnt/disk01 type ext3 (rw,relatime)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/suma/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=suma)

---

### Post by dabl on 2008-11-19
> Partition 1 does not end on cylinder boundary.

This is a bad thing - it explains some or all of your problems with that 500GB drive.

You need to back up all data on it and re-partition it to fix this. I use a GParted Live CD -- you can boot any Live CD that has GParted or QParted on it, and partition that drive as you wish.

---

### Post by Green_Star on 2008-11-19
> **dabl said:**
> This is a bad thing - it explains some or all of your problems with that 500GB drive.

You need to back up all data on it and re-partition it to fix this. I use a GParted Live CD -- you can boot any Live CD that has GParted or QParted on it, and partition that drive as you wish.

Yes, I observed that, is there any way I can do that with ubuntu live cd? I have no way of backing up 500GB,I will try my best. 

I just tried fsck without mounting that drive and my system hanged. This is bad because **Ubuntu should tell me that it is bad disk instead of just hanging my whole system.**

---

### Post by taurus on 2008-11-19
Since /dev/sdc is a third harddrive, you can repartition/reformat it without booting the LiveCD since your Ubuntu is located on /dev/sda3.  And looks like you should have enough space on /dev/sdb1 (/mnt/disk01) to move your files from /dev/sdc to it.

But I guess you have to do the copying from LiveCD since everytime you try to move something off /dev/sdc, it freezes.

Boot your machine with the LiveCD.  Open a terminal and run

```
sudo mkdir /media/sdb1 /media/sdc1 /media/sdc2 /media/sdc3
sudo mount -t ext3 /dev/sdb1 /media/sdb1
sudo mount -t ntfs-3g /dev/sdc1 /media/sdc1
sudo mount -t ext3 /dev/sdc2 /media/sdc2
sudo mount -t ext3 /dev/sdc3 /media/sdc3
df -h
```
Once you have moved everything out of /dev/sdc into /media/sdb1, you need to unmount those three partitions on /dev/sdc.

```
sudo umount /dev/sdc1 /dev/sdc2 /dev/sdc3
```
Then, fire up gparted from the LiveCD (System -> Administration) and delete those three partitions on /dev/sdc.  Then, create new partitions and format them to whatever filesystem you want.  Once you're done, reboot and then mount them through /etc/fstab.

---

### Post by hardyn on 2008-11-19
What about checking out motherboard firmware updates?

---

### Post by Green_Star on 2008-11-19
Thanks taurus. I have around 20GB of space if I combine my both PATA drives. I am looking a way to do it without loosing much data from SATA.

I do not see any option about "RAID" or "AHCI" or "Legacy IDE" in my bios, I have 'auto' only.

---

### Post by psusi on 2008-11-19
> **dabl said:**
> This is a bad thing - it explains some or all of your problems with that 500GB drive.


No it is not.  Partitioning tools tend to align partitions to cylinder boundaries out of tradition.  There is no real reason to do so, and no harm in not doing so.  These days the cylinder/sector/head concept doesn't even exist except as a farcical carryover from days gone by anyhow.

The problem is in the driver, the hardware, or the interaction between the two.

---

### Post by Green_Star on 2008-11-20
Thank you. So it may not be partition thing. 

So, can some one suggest a good live recovery cd? That should include all tools liek gparted, fsck(graphical frontend?) and any thing useful like creating disk images etc.

> **psusi said:**
> No it is not.  Partitioning tools tend to align partitions to cylinder boundaries out of tradition.  There is no real reason to do so, and no harm in not doing so.  These days the cylinder/sector/head concept doesn't even exist except as a farcical carryover from days gone by anyhow.

The problem is in the driver, the hardware, or the interaction between the two.

---

