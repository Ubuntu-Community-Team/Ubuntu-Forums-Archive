---
title: "External HDD doesn't mount in 12.04"
date: 2013-06-01
forum: Hardware
---

### Post by MZ250Supa5 on 2013-06-01
I have just upgraded the hardware on my system to a 2 TB HDD (internal) and now wish to transfer the data I have on the original 1 TB HDD to that new disk.  I have put the previous 1 TB disk in a usb caddy, and plugged it in, it shows up in the disk manager, but I cannot mount it.  It's formatted as ext4, and also has a Windows partition, and, crucially automounts on Ubuntu 10.04 with no problems, howver on 12.04 there seems to be no way to get this external drive to mount.

Does the fact that the disk I now wish to mount as an external usb hdd has an entire OS on it affect matters, or is this just another example of how bad Ubuntu has become? I should add that I am using the Gnome 3 Classic desktop, (I really don't like Unity) and I know this is buggy, so this too may be part of the issue. It's a shame that Ubuntu has become so user-unfriendly, with features that used to 'just work' being hidden behind obscure menus or just not being there at all.  What ever happend to 'if it ain't broke, don't fix it'?

---

### Post by sudodus on 2013-06-01
I assume that right now you are booting the computer from a CD/DVD or USB pendrive.

If you are prepared to use a terminal window, we might be able to solve your problem. I think you need superuser privileges to mount it.

Identify the drive with the following commands

```
 sudo fdisk -lu
```
```
 sudo parted -l
```

I guess one of the drives is /dev/sda and the other one /dev/sdb (unless the boot drive is /dev/sdb, then it is probably /dev/sdc). Let us assume that it is /dev/sdb

Then you need to identify the partitions for example

/dev/sdb1 (windows recovery)
/dev/sdb2 (windows)
/dev/sdb3 (extended)
/dev/sdb5 (ubuntu root partition)
/dev/sdb6 (swap)

Mount the root partition with the following command

```
 sudo mount -t auto /dev/sdb5 /mnt
```

-o-

But what do you want to do? Would you actually like to clone the drive to the new one? And then afterwards edit or fix the partition table so that you can use the larger size? Then you should not mount any partition, but select a tool for the cloning and use that.

Or do you want to start with new installations of Windows and Ubuntu and only transfer your data files? Then mounting of partitions is the right way to go.

---

### Post by MZ250Supa5 on 2013-06-01
Hi Sudodus, thanks for getting back to me so promptly.  I am happy to use a terminal window, and I have followed your directions so far, however, when I try and mount the partition using the command you provided I get 'mount:you must specify the filesystem type'. I'm not actually using a live CD or a usb at the moment, as I have installed 12.04 on a 2 TB HDD and now wish to transfer the files over from the 1TB HDD in a caddy to the new install, so a mounting of the disk is what is required.  The WIndows files will be transferred to a WIndows parrtion I shall be putting on a different drive on a different machine - it's major network overhaul time here!

---

### Post by sudodus on 2013-06-01
> **MZ250Supa5 said:**
> Hi Sudodus, thanks for getting back to me so promptly.  I am happy to use a terminal window, and I have followed your directions so far, however, when I try and mount the partition using the command you provided I get 'mount:you must specify the filesystem type'. I'm not actually using a live CD or a usb at the moment, as I have installed 12.04 on a 2 TB HDD and now wish to transfer the files over from the 1TB HDD in a caddy to the new install, so a mounting of the disk is what is required.  The WIndows files will be transferred to a WIndows parrtion I shall be putting on a different drive on a different machine - it's major network overhaul time here!

OK, so you have already tried the easy things, and they do not work. Maybe there is some issue with the caddy system.

- Is is a desktop or laptop computer (or should I ask: Can you connect the 1 GB drive directly 'internally' to a SATA port)?

- Anyway, I might see something if you post the output of the following commands.

```
 sudo fdisk -lu
```
```
 sudo parted -l
```
```
 sudo blkid
```
```
df
```

---

### Post by MZ250Supa5 on 2013-06-01
The output from sudo fdisk -lu is:

ceridwen@ceridwen:~$ sudo fdisk -lu
[sudo] password for ceridwen: 

Disk /dev/sda: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x000a616f

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048  3890255871  1945126912   83  Linux
/dev/sda2      3890257918  3907028991     8385537    5  Extended
Partition 2 does not start on physical sector boundary.
/dev/sda5      3890257920  3907028991     8385536   82  Linux swap / Solaris
Note: sector size is 4096 (not 512)
Warning: ignoring extra data in partition table 5
Warning: ignoring extra data in partition table 5
Warning: ignoring extra data in partition table 5
Warning: invalid flag 0x7f96 of partition table 5 will be corrected by w(rite)

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 15200 cylinders, total 244190646 sectors
Units = sectors of 1 * 4096 = 4096 bytes
Sector size (logical/physical): 4096 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x72217221

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *        2048   138353295   553404992    7  HPFS/NTFS/exFAT
/dev/sdb2       138354686  1953523711  2965708808    5  Extended
/dev/sdb5   ?  3896317421  8033992553  3665798644   b6  Unknown
ceridwen@ceridwen:~$ 

From sudo parted -l:

ceridwen@ceridwen:~$ sudo parted -l
[sudo] password for ceridwen: 
Model: ATA ST2000DM001-1CH1 (scsi)
Disk /dev/sda: 2000GB
Sector size (logical/physical): 512B/4096B
Partition Table: msdos

Number  Start   End     Size    Type      File system     Flags
 1      1049kB  1992GB  1992GB  primary   ext4            boot
 2      1992GB  2000GB  8587MB  extended
 5      1992GB  2000GB  8587MB  logical   linux-swap(v1)


Error: Cannot have a partition outside the disk!                          

ceridwen@ceridwen:~$ 

From sudo blkid:

ceridwen@ceridwen:~$ sudo blkid
[sudo] password for ceridwen: 
/dev/sda1: UUID="4c866981-7176-4d1d-ae66-dac17430a9c5" TYPE="ext4" 
/dev/sda5: UUID="3d2a0270-ed16-421b-a320-6622b3b95ce3" TYPE="swap" 
ceridwen@ceridwen:~$ 

and from df;

ceridwen@ceridwen:~$ df
Filesystem      1K-blocks    Used  Available Use% Mounted on
/dev/sda1      1914604924 9730284 1807618296   1% /
udev              4046740      12    4046728   1% /dev
tmpfs             1635412    1180    1634232   1% /run
none                 5120       0       5120   0% /run/lock
none              4088524     112    4088412   1% /run/shm
ceridwen@ceridwen:~$ 


Sorrym I don't yet know how to post the output in the boxes that most people seem to use  - I have tried to find out, but there seems to be no place that guides 'how to post'.

I'm using a desktop computer, and I am able to connect directly to a SATA connector on the mobo if needs be.

---

### Post by sudodus on 2013-06-01
Please post the output between code tags like this
 
[noparse]```
output
```[/noparse]
 
to get output like this
 
```
output
```

You can mark the text and click on the # icon at the top of the editing window (in advanced mode)

---

### Post by sudodus on 2013-06-01
```
ceridwen@ceridwen:~$ sudo fdisk -lu
[sudo] password for ceridwen: 

Disk /dev/sda: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x000a616f

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048  3890255871  1945126912   83  Linux
/dev/sda2      3890257918  3907028991     8385537    5  Extended
Partition 2 does not start on physical sector boundary.
/dev/sda5      3890257920  3907028991     8385536   82  Linux swap / Solaris
[COLOR=#ff0000]Note: sector size is 4096 (not 512)
Warning: ignoring extra data in partition table 5
Warning: ignoring extra data in partition table 5
Warning: ignoring extra data in partition table 5
Warning: invalid flag 0x7f96 of partition table 5 will be corrected by w(rite)
[/COLOR]
Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 15200 cylinders, total 244190646 sectors
Units = sectors of 1 * 4096 = 4096 bytes
Sector size (logical/physical): 4096 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x72217221

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *        2048   138353295   553404992    7  HPFS/NTFS/exFAT
/dev/sdb2       138354686  1953523711  2965708808    5  Extended
[COLOR=#ff0000]/dev/sdb5   ?  3896317421  8033992553  3665798644   b6  Unknown
[/COLOR]ceridwen@ceridwen:~$ 

From sudo parted -l:

ceridwen@ceridwen:~$ sudo parted -l
[sudo] password for ceridwen: 
Model: ATA ST2000DM001-1CH1 (scsi)
Disk /dev/sda: 2000GB
Sector size (logical/physical): 512B/4096B
Partition Table: msdos

Number  Start   End     Size    Type      File system     Flags
 1      1049kB  1992GB  1992GB  primary   ext4            boot
 2      1992GB  2000GB  8587MB  extended
 5      1992GB  2000GB  8587MB  logical   linux-swap(v1)


[COLOR=#ff0000]Error: Cannot have a partition outside the disk!      [/COLOR]                    

ceridwen@ceridwen:~$ 

From sudo blkid:

ceridwen@ceridwen:~$ sudo blkid
[sudo] password for ceridwen: 
/dev/sda1: UUID="4c866981-7176-4d1d-ae66-dac17430a9c5" TYPE="ext4" 
/dev/sda5: UUID="3d2a0270-ed16-421b-a320-6622b3b95ce3" TYPE="swap" 
ceridwen@ceridwen:~$ 

and from df;

ceridwen@ceridwen:~$ df
Filesystem      1K-blocks    Used  Available Use% Mounted on
/dev/sda1      1914604924 9730284 1807618296   1% /
udev              4046740      12    4046728   1% /dev
tmpfs             1635412    1180    1634232   1% /run
none                 5120       0       5120   0% /run/lock
none              4088524     112    4088412   1% /run/shm
ceridwen@ceridwen:~$ 

```

This shows that there is something wrong, or should we say something that cannot be managed by linux.

```
[COLOR=#ff0000]/dev/sdb5   ?  3896317421  8033992553  3665798644   b6  Unknown[/COLOR]
```

Is this partition mounted and read by Windows? Is it maybe a dynamic partition? But such a partition should not be managed by Ubuntu 10.04 either, so you have to use Windows to copy from it. Or has it been damaged somehow? Or maybe there has always been some non-standard feature, that worked as long as you used the same system to manage it? [I][B]Can it still be mounted and read by Ubuntu 10.04 (for example booted from a live CD/DVD/USB drive)?
[/B][/I]
What about

```
/dev/sdb1   *        2048   138353295   553404992    7  HPFS/NTFS/exFAT
```

It that also impossible to mount and read from 12.04, but available from 10.04?

You wrote that the 1 TB drive mounts in Ubuntu 10.04 without problem. Then I think you need to use Ubuntu 10.04 to get the data from it.

I must admit that I don't really understand this, but maybe [COLOR=#ff0000]someone with more experience can jump in a help us[/COLOR] :-)

Good luck :-)

---

### Post by MZ250Supa5 on 2013-06-01
Thanks for your help Sudodus, I'll get to the bottom of this, it's not insurmountable.  I shall just have to install it in a machine and boot it up and transfer all the files over my network.  It seems I was mistaken about it being available from 10.04 - the nachine I have 10.04 on also has a 1 TB HDD and I got confused!.

---

### Post by sudodus on 2013-06-01
Maybe they are dynamic partitions, created and readable by Windows. Let us hope so :-)

---

