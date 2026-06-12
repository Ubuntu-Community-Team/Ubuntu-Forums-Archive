---
title: "The disk drive for /root is not ready or not present."
date: 2010-09-11
forum: Hardware
---

### Post by Sciezyna on 2010-09-11
I am newbie in Linux, I know some about hardware and Windows but Windows is almost the past.

I have Ubuntu 10.04 GNOME installed on separate disk from Windows XP.

Ubuntu -> /root 10GB; Swap 8GB; /home = 300GB (/dev/sdb1, /dev/sdb2; /dev sdb3)

The install went well and Ubuntu worked well.

Windows shows (In System/Administration/Disk Utility) on /dev/sda1; windows data /dev/sda2 - none is mounted.

Recently I used 50GB of free space on /dev/sda for special usage in Ubuntu. Partitioned it with GParted. I tried to mount it with GParted but something went wrong (just did not know how and where to mount it) and I pressed in GParted 'Unmount All'. Seemingly nothing happened... I mounted the new partition though Disk Utility on /media/utemp and it works ok.

I needed to restart the pc and I did so from Ubuntu. PC went into BIOS etc., then displayed start menu with all selections as always: Linux, Linux recovery, Memtest64+, Memtest64+ serial, Windows.

After I selected Linux from the top menu, a large white cursor blinked for ~5 seconds and a message flashed on top of the screen but I could not read it it was to fast. I then got the UBUNTU ........  logo and the message:

The disk drive for /root is not ready yet or not present.
Continue to wait or press S to skip mounting or M for mount recovery.

I pressed S Ubuntu started and all seem to work normally. I think I screwed something with the mounting in GParted. The above message show now each time the pc is restarted.

I beg for an experienced helping hand here. I read about mounting but could not comprehend it yet... and GParted did what I asked it to do...

Thanks

---

### Post by efflandt on 2010-09-11
I sometimes get that message when booting from a USB hard drive (maybe the drive has not spun up and stabilized yet), but I do nothing and in a few seconds it continues fine.  So it could be that your slave drive just takes slightly longer to spin up than Linux is expecting.

---

### Post by Sciezyna on 2010-09-11
Thanks for quick replay.
I will wait on the bootprocess longer and see what is happening. Will post message about the result.

Regards

---

### Post by Sciezyna on 2010-09-11
The message is there after 30 minutes of waiting. There must be something else the disk with the root mount is SATA, Disk Utility test comes good.

---

### Post by CharlesA on 2010-09-11
Go into recovery mode and drop to a root shell.

Check what /etc/fstab looks like:

```
nano /etc/fstab
```

The "root" of the file system, should be mounted as "/"

---

### Post by Sciezyna on 2010-09-11
Do I have to go to recovery mode? The system runs after I press the "S" to skip...

The fstab now (not in recovery) looks like:

UUID=34a0fe1a-a9d6-422d-93b4-3c87d4becdb9 / ext4 defaults 0 1
UUID=4aca7e80-8046-4de7-99ec-95e5c424eb42 swap swap sw 0 0
UUID=6f2e0776-5768-4eb4-8a49-72975b7b2b0d /home ext4 defaults 0 2
UUID=47de0cdd-9ef8-4c89-bd00-9f5fc3175d61 /root ext4 defaults 0 0
/dev/fd0 /media/floppy0 vfat noauto 0 0

Hm.. the first disk is the one "34a0fe1a-a9d6-422d-93b4-3c87d4becdb9" is the /dev/sdb1 where ubuntu is installed and it is mounted at /
but what about the /root mount? is this correct? isn't / the same as /root ?

I am lost

Thanks

---

### Post by CharlesA on 2010-09-11
> **Sciezyna said:**
> Do I have to go to recovery mode? The system runs after I press the "S" to skip...

The fstab now (not in recovery) looks like:

UUID=34a0fe1a-a9d6-422d-93b4-3c87d4becdb9 / ext4 defaults 0 1
UUID=4aca7e80-8046-4de7-99ec-95e5c424eb42 swap swap sw 0 0
UUID=6f2e0776-5768-4eb4-8a49-72975b7b2b0d /home ext4 defaults 0 2
UUID=47de0cdd-9ef8-4c89-bd00-9f5fc3175d61 /root ext4 defaults 0 0
/dev/fd0 /media/floppy0 vfat noauto 0 0

Hm.. the first disk is the one "34a0fe1a-a9d6-422d-93b4-3c87d4becdb9" is the /dev/sdb1 where ubuntu is installed and it is mounted at /
but what about the /root mount? is this correct? isn't / the same as /root ?

I am lost

Thanks

No, /root isn't the same as /.

The first mountpoint is "/" which is the root of the file system. I don't know why you are trying to mount a device to "/root"

Can you run this and post the output:

```
sudo fdisk -l
```
```
sudo blkid /dev/sd??
```

---

### Post by Sciezyna on 2010-09-11
> **CharlesA said:**
> No, /root isn't the same as /.

The first mountpoint is "/" which is the root of the file system. I don't know why you are trying to mount a device to "/root"

Can you run this and post the output:

```
sudo fdisk -l
```

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x01880187

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        8924    71681998+   7  HPFS/NTFS
/dev/sda2            8925       30890   176440201    7  HPFS/NTFS
/dev/sda3           30891       37391    52219282+  83  Linux
/dev/sda4           37392       38913    12225465    7  HPFS/NTFS

Disk /dev/sdb: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000c0fbe

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        1275    10241406   83  Linux
/dev/sdb2            1276        2295     8193150   82  Linux swap / Solaris
/dev/sdb3            2296       38913   294134085   83  Linux

Disk /dev/sdc: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x104a1049

   Device Boot      Start         End      Blocks   Id  System

Disk /dev/sdd: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x36c50ed5

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1   *           1        8924    71681998+   7  HPFS/NTFS
/dev/sdd2            8925       38913   240886642+   7  HPFS/NTFS


```
sudo blkid /dev/sd??
```

/dev/sda1: LABEL="CLONED" UUID="144CB8B64CB893C8" TYPE="ntfs" 
/dev/sda2: LABEL="CLON_Data" UUID="6EC4F08CC4F057B3" TYPE="ntfs" 
/dev/sda3: LABEL="utemp" UUID="8973c548-b2d1-4021-b5a8-332b6716445d" TYPE="ext4" 
/dev/sda4: LABEL="NITS-Scratch" UUID="4460E63570862801" TYPE="ntfs" 
/dev/sdb1: UUID="34a0fe1a-a9d6-422d-93b4-3c87d4becdb9" TYPE="ext4" 
/dev/sdb2: UUID="4aca7e80-8046-4de7-99ec-95e5c424eb42" TYPE="swap" 
/dev/sdb3: UUID="6f2e0776-5768-4eb4-8a49-72975b7b2b0d" TYPE="ext4" 
/dev/sdd1: LABEL="XP_SYS" UUID="144CB8B64CB893C8" TYPE="ntfs" 
/dev/sdd2: LABEL="XP_DATA" UUID="487C72E97C72D164" TYPE="ntfs" 

I do not know what the mounting to /root is and why. As I said in the first post I am very new to Linux.

The system is installed on separate disk sdb - there is /, swap, and /home

I read a bit about fstab structure but could not find if there is the use of comment like # starting comment.

What if I commented the line mounting the /root?

Thanks

---

### Post by Sciezyna on 2010-09-11
Well now,

# is a comment sign and works in /etc/fstab.
My Ubuntu install is young so I took a risk and commented the line mounting to the /root.
No more message the system boots quick and clean. That will be a puzzle for me but I will keep searching.

Thanks, I am not marking it as a solved yet because I need to find why in the fstab was that line mounting /root and which disk is this?

---

### Post by CharlesA on 2010-09-11
I don't see that drive in fdisk or blkid.

I don't know why that line was in there. Could you have had a usb drive or something hooked up when you installed Ubuntu?

Normally if something is added automatically to fstab during install it looks something like this here:

```
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=a27ef6de-0b37-4556-ae53-367841dc2735 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=5fcefb26-c2ea-4170-be83-e45f212ba51a none            swap    sw              0       0
```

Also note: It doesn't look like there is any partitions on the drive listed as /dev/sdc

---

### Post by Sciezyna on 2010-09-11
One of the reasons that the message from the title appears at boot time is that during boot the system tests consistency of all drives listed in /etc/fstab. If not all drives are tested or say not found as explained below this message show up.



It is my strong guess but this is what probalby happened in my case:

Needed extra HDD partition 'utemp' but to on /media - suggestion given here.
I used GParted to add a partition (create partition, format).

I tried to mount then deleted and so on,  changed, deleted and created... (I did try to mount it not on /media but that did not work) Once, I guess, I mounted it on /root/utemp - Applied action, then deleted it again.

I did finally mount the new partition with GNOME Disk Utility (unfortunately on /media/utemp) default option.

I think that this line in /etc/fstab with the non-existing by now drive was left by GParted...

During boot the system kept waiting but could not find this drive, hence the message.

The confusion was caused by the option "S" in the message's prompt which caused normal system start up - there was something wrong but not vital.

I will quote a signature of one o the older users on this forum something to this effect:

"Linux believes that you know exactly what you are doing!"

Be carefull

Thank you for all your help.

---

