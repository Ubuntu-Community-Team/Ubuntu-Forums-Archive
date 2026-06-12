---
title: "HDD Problems"
date: 2011-06-02
forum: Hardware
---

### Post by matt.mtbr on 2011-06-02
I have been having some problems mounting my hard drives in Natty.

Neither the 2nd HDD or the 2nd Partition of the Boot disk can be accessed.
Both appear in gparted and are apparently mounted
One claims to have 32 GB of data on however there is nothing visible when browsed through except a tiny unopenable lost and found file.
The other does not show up at all and cannot be unmounted because it is "busy"

Everything was fine until I attempted to have the devices mounted automatically using pysdm. The 2nd HDD had a tiny partition and a large unallocated section although data must have been saving to this part.

does anyone know a way to fix this? Everything is backed up but so far any attempt to format everything has failed.

Thanks

---

### Post by Davaross on 2011-06-03
I recently encountered an issue on my desktop similar to the one you are describing, believe it or  not the soloution for me was to use my old xp professional install disk to delete all the new partitions and then create a new ntfs partition which could then be deleted from a gparted live cd.
You say you have all of your data backed up so you have nothing to lose by trying this.
Hope this helps,
Davaross

---

### Post by coffeecat on 2011-06-03
> **matt.mtbr said:**
> Everything was fine until I attempted to have the devices mounted automatically using pysdm.

That may very well be the problem. Pysdm was first developed in 2005 and seems to have had no development done on it since. Like other apps in the repositories which purport to write /etc/fstab lines for you, it seems to be unreliable.

Please post the output of these three terminal commands and we can take it from there:

```
cat /etc/fstab
sudo fdisk -lu
sudo blkid
```

---

### Post by matt.mtbr on 2011-06-03
matt@Matt:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc                                       /proc           proc  nodev,noexec,nosuid       0  0  
# / was on /dev/sda5 during installation
UUID=791be182-197b-4a99-affa-a6162e1f39b8  /               ext4  errors=remount-ro         0  1  
# swap was on /dev/sda6 during installation
UUID=ef3465ce-8755-4b2f-9922-0d398cf9116e  none            swap  sw                        0  0  
/dev/fd0                                   /media/floppy0  auto  rw,user,noauto,exec,utf8  0  0  
/dev/sdb1                                  /media          ext2  defaults                  0  0  
/dev/sda1                                  /media/sda1     ext2  defaults                  0  0  
/dev/sda2                                  /media/sda2     ext2  defaults                  0  0  

matt@Matt:~$ sudo fdisk -lu
[sudo] password for matt: 

Disk /dev/sda: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000a1d2a

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63  3907024064  1953512001   83  Linux

Disk /dev/sdb: 750.2 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders, total 1465149168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x43684367

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1            2048   682756095   341377024   83  Linux
/dev/sdb2   *   682758142  1465147391   391194625    5  Extended
/dev/sdb5       682758144  1456762879   387002368   83  Linux
/dev/sdb6      1

matt@Matt:~$ sudo blkid
/dev/sda1: LABEL="Magic" UUID="300ec0d3-f619-47f5-96b6-58c27d887fca" TYPE="ext4" 
/dev/sdb1: UUID="32ccddaf-8e31-4116-be36-6704c86d8dfa" TYPE="ext4" 
/dev/sdb5: UUID="791be182-197b-4a99-affa-a6162e1f39b8" TYPE="ext4" 
/dev/sdb6: UUID="ef3465ce-8755-4b2f-9922-0d398cf9116e" TYPE="swap"

---

### Post by coffeecat on 2011-06-03
I'll just repost your outputs in code tags so that I can read them. The formatting gets lost if you don't. I'll post back once I've made sense of it. In the meantime here's something on BBCode:

[http://ubuntuforums.org/misc.php?do=bbcode](http://ubuntuforums.org/misc.php?do=bbcode)


```
matt@Matt:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc                                       /proc           proc  nodev,noexec,nosuid       0  0  
# / was on /dev/sda5 during installation
UUID=791be182-197b-4a99-affa-a6162e1f39b8  /               ext4  errors=remount-ro         0  1  
# swap was on /dev/sda6 during installation
UUID=ef3465ce-8755-4b2f-9922-0d398cf9116e  none            swap  sw                        0  0  
/dev/fd0                                   /media/floppy0  auto  rw,user,noauto,exec,utf8  0  0  
/dev/sdb1                                  /media          ext2  defaults                  0  0  
/dev/sda1                                  /media/sda1     ext2  defaults                  0  0  
/dev/sda2                                  /media/sda2     ext2  defaults                  0  0  

matt@Matt:~$ sudo fdisk -lu
[sudo] password for matt: 

Disk /dev/sda: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000a1d2a

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63  3907024064  1953512001   83  Linux

Disk /dev/sdb: 750.2 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders, total 1465149168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x43684367

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1            2048   682756095   341377024   83  Linux
/dev/sdb2   *   682758142  1465147391   391194625    5  Extended
/dev/sdb5       682758144  1456762879   387002368   83  Linux
/dev/sdb6      1

matt@Matt:~$ sudo blkid
/dev/sda1: LABEL="Magic" UUID="300ec0d3-f619-47f5-96b6-58c27d887fca" TYPE="ext4" 
/dev/sdb1: UUID="32ccddaf-8e31-4116-be36-6704c86d8dfa" TYPE="ext4" 
/dev/sdb5: UUID="791be182-197b-4a99-affa-a6162e1f39b8" TYPE="ext4" 
/dev/sdb6: UUID="ef3465ce-8755-4b2f-9922-0d398cf9116e" TYPE="swap"
```

---

### Post by coffeecat on 2011-06-03
First problem. When you installed Ubuntu to the 750GB HD it was designated sda, but now it appears as sdb. Your 2000GB disk, with one single partition appears as sda, but I suspect it was originally sdb. This wouldn't matter if fstab used only UUIDs, but it doesn't. This bit of fstab:

```
/dev/sdb1                                  /media          ext2  defaults                  0  0  
/dev/sda1                                  /media/sda1     ext2  defaults                  0  0  
/dev/sda2                                  /media/sda2     ext2  defaults                  0  0  
```... is really problematic. sdb1 is mounted to /media, but fstab is trying to mount sda1 and sda2 (which doesn't exist) to subfolders in /media. This is impossible if /media itself is being used as a mountpoint. First moral of this: never use /media as a mountpoint, always subfolders within /media. Did pysdm write this bit of fstab? If so, uninstall pysdm **now**.

The next problem is that those lines are trying to mount those partitions as ext2, whereas they are ext4. I suspect that the '/dev/sda1' line originally referred to the first partition on the 2000GB drive, but goodness knows what /dev/sda2 refers to. Perhaps your extended partition? If so, you can't do that; see below.

Only /dev/sdb1, your 350GB sda1 partition (=326GiB) is being mounted and that improperly as an ext2 filesystem. The reason you can't access it is that it is owned by root. The lost+found folder is part of the ext* fileystem and is also owned by root - that's why you can't open it.

By the way - you missed out a bit of the output of fdisk - the line for sdb6. But that is of small consequence.

There is no usable second partition on the "boot" disk - see below. Fyi your partitions are:

sda1 - Approx 2000GB. This is not being mounted, or if mounted is mounted on /media/sda1, but the use of /media as a mountpoint as well is preventing access.

sdb1 - Approx 350GB. Mounted on /media. This is the one you can see but not access. The 32GB of data is probably the filesystem itself. Normally this is only 5% of the available space, so 32GB seems a bit excessive.

sdb2 - your extended partition. You can't mount this - it's simply a "container" for the logical partitions, which are:

sdb5 - your Ubuntu root partition, approx 386GB
sdb6 - your swap partition.

Solution - you need to edit /etc/fstab to remove those last three spurious lines, replacing them with ones that use UUIDs and which mount the partitions as ext4.

Then, to be able to access the two partitions sda1 and sdb2, you need to do one of two things. Either, use mount options that give you ordinary user read-write access. Or - chmod and chown the mounted partitions with appropriate ownership and permissions. Either works equally well.

Post back if you need help with any of that.

---

### Post by matt.mtbr on 2011-06-03
Thanks for the quick reply, i think I do need some help.

What are the lines that I should have?

---

### Post by coffeecat on 2011-06-03
> **matt.mtbr said:**
> Thanks for the quick reply, i think I do need some help.

I am being told permission denied, the file is read only and apparently I do not own it and cannot alter this.

What file? If you mean the  lost+found folder, leave it be. You don't need to access it - you don't need it. It's used by the system to store recovered data in the event of filesystem corruption. However, it is very easy to take ownership of the partition so that you can create new folders and write to them. Which bit do you need help with, editing fstab or taking ownership of the partition, or both? We need to sort out fstab before getting you access, or we can gain you access when you edit fstab.

---

### Post by matt.mtbr on 2011-06-03
I can edit fstab but I don't know what to put in place of the deleted lines.

Is there any way of changing linix back to sda? is there any point?

---

### Post by coffeecat on 2011-06-03
> **matt.mtbr said:**
> I can edit fstab but I don't know what to put in place of the deleted lines.

Is there any way of changing linix back to sda? is there any point?

It would depend on your BIOS settings and which drive is connected to which SATA header. If you use UUIDs in fstab there's little point. I like to see my "master" drive as sda, but that's because it makes life less confusing.

OK - to business. Open fstab with;

```
gksu gedit /etc/fstab
```Remove these three lines:

```
/dev/sdb1                                  /media          ext2  defaults                  0  0
/dev/sda1                                  /media/sda1     ext2  defaults                  0  0
/dev/sda2                                  /media/sda2     ext2  defaults                  0  0
```**EDIT**: Oops, you don't have a /media/sdb1:

```
sudo mkdir /media/sdb1
```**End-edit**

Now add these lines:

```
UUID=300ec0d3-f619-47f5-96b6-58c27d887fca     /media/sda1     ext4     defaults     0 2
UUID=32ccddaf-8e31-4116-be36-6704c86d8dfa     /media/sdb1     ext4     defaults     0 2
```I've kept the options simple, but the disadvantage is that those partitions will be mounted and owned by root unless we do the next step.

Save the edited file and exit gedit. Now run this command from the terminal:

```
sudo mount -a
```Your two partitions will mount and icons will appear on the desktop but as yet you won't be able to access them. Now, from the terminal:

```
sudo chown yourusername: /media/sda1
sudo chown yourusername: /media/sdb1
sudo chmod 777 /media/sda1
sudo chmod 777 /media/sdb1
```Substitute your login/account name for "yourusername" and don't forget the trailing colons after your name in the first two commands. That sets ownership of your default group. The chmod commands are not necessary if you are the only account holder but they do prevent permissions issues. They are very permissive permissions though.

It looks as though the chown and chmod commands are acting on the mountpoints, the folders /media/sda1 and /media/sdb1. Rather curiously they do not - they change ownership and permissions of the actual filesystem and now you will be able to write to both partitions. Simply ignore the lost+found folders. Even if you delete them with root privileges, they will be re-created next time there's a filesystem check.

---

### Post by matt.mtbr on 2011-06-03
I am getting this error when I attempt to mount

```

matt@Matt:~$ sudo mount -a
[sudo] password for matt: 
mount: special device UUID=300ec0d3-f619-47f5-96b6-58c27d887fca does not exist
mount: mount point /media/sdb1 does not exist
matt@Matt:~$ 


```

---

### Post by coffeecat on 2011-06-03
> **matt.mtbr said:**
> I am getting this error when I attempt to mount

```

matt@Matt:~$ sudo mount -a
[sudo] password for matt: 
mount: special device UUID=300ec0d3-f619-47f5-96b6-58c27d887fca does not exist
mount: mount point /media/sdb1 does not exist
matt@Matt:~$ 


```

Yes, sorry, I forgot you didn't have a /media/sdb1. I edited my post just before you posted to include that. Have another look. It's about halfway through.

---

### Post by matt.mtbr on 2011-06-03
It takes a very long time to mount...

Is this normal?

---

### Post by coffeecat on 2011-06-03
> **matt.mtbr said:**
> It takes a very long time to mount...

Is this normal?

No, it should be near-instantaneous. Is this just sdb1 or both the partitions? Does it mount eventually or is the mounting just hanging on you? It could be that the filesystem needs checking.

---

### Post by matt.mtbr on 2011-06-03
```

matt@Matt:~$ sudo mount -a
[sudo] password for matt: 
mount: block device /dev/fd0 is write-protected, mounting read-only
mount: you must specify the filesystem type
mount: special device UUID=300ec0d3-f619-47f5-96b6-58c27d887fca does not exist
mount: special device UUID=32ccddaf-8e31-4116-be36-6704c86d8dfa does not exist

```

For both I think, I am not sure.

---

### Post by coffeecat on 2011-06-03
> **matt.mtbr said:**
> ```

mount: special device UUID=300ec0d3-f619-47f5-96b6-58c27d887fca does not exist
mount: special device UUID=32ccddaf-8e31-4116-be36-6704c86d8dfa does not exist

```

They certainly existed when you posted the output of 'sudo blkid', so I don't know why you should get that error. Post the output of:

```
sudo blkid
cat /etc/fstab
```So that we can double-check your revised /etc/fstab and make sure something odd hasn't happened with the UUIDs.

I have to log off now, but I will check this thread in the morning.

---

### Post by matt.mtbr on 2011-06-04
Ubuntu is now not starting, the loadibg screen before login does not leave.

I will do a clean install and see where that leaves me.

---

### Post by coffeecat on 2011-06-04
> **matt.mtbr said:**
> Ubuntu is now not starting, the loadibg screen before login does not leave.

I'm sorry to hear that. This morning I realised that your sda1 and sdb1 partitions may still have been mounted in /media/sda1 and /media, but I would have thought that you would have got a "partition already mounted" type error.

Looking at the package description of pysdm, I see this:

> PySDM is a PyGTK-based Storage Device Manager that allows full customization
of hard disk mount points without the need to edit fstab manually.
[B]It also allows the creation of udev rules for dynamic configuration of
storage devices.[/B]I've emboldened the bit that worries me. If it's messing with udev rules, goodness knows what damages it's done. PySDM is best left uninstalled, imo.

> **matt.mtbr said:**
>  I will do a clean install and see where that leaves me.

Good luck with that.

---

### Post by matt.mtbr on 2011-06-04
```

etmatt@matt-P5Q-DELUXE:~$ sudo blkid
[sudo] password for matt: 
/dev/sda2: UUID="e62be98e-7c2a-4407-83ea-87e6ccad5528" TYPE="ext4" 
/dev/sda3: UUID="9b3d6d30-d2ae-4872-92aa-7ca1135ef9df" TYPE="swap" 
/dev/sdb1: UUID="50f9bf47-dfef-454f-8afa-60e1371d87b1" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdb5: UUID="791be182-197b-4a99-affa-a6162e1f39b8" TYPE="ext4" 
/dev/sdb6: UUID="ef3465ce-8755-4b2f-9922-0d398cf9116e" TYPE="swap" 
matt@matt-P5Q-DELUXE:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda2 during installation
UUID=e62be98e-7c2a-4407-83ea-87e6ccad5528 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda3 during installation
UUID=9b3d6d30-d2ae-4872-92aa-7ca1135ef9df none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0


```

Re installed and run those commands the 2 TB sda drive is now the boot drive and the other drive has been left. I will put in a partition to the 2 TB drive as I continue the installation but I want to sort the main problems out first.

I will not be reinstalling the pysdm...

---

