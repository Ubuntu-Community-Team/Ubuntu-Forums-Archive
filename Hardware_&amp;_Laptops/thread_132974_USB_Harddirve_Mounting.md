---
title: "USB Harddirve Mounting"
date: 2006-02-19
forum: Hardware &amp; Laptops
---

### Post by AdministratorX on 2006-02-19
Hello,

I have three USB harddrives attached to my system I can access all but one of them. It is a WD 800BB External from Western Digital (80 Gig HD). The system displays it as /dev/sdc. It is formated as NTFS (The same as the other two), however it will not auto mount under gnome, nor will it allow me to mount it in a vterm even using sudo. Can anyone please advise me on getting this device to mount.

Thanks

---

### Post by Sutekh on 2006-02-19
What actual commands have you used tried to mount it?  And what errors did you recieve from trying them?

Also can you supply the output of```
sudo fdisk -l 
```and```
cat /etc/fstab
```This will help determine the necessary mount options.

---

### Post by AdministratorX on 2006-02-19
Hello,

Here is the output from the commands you requested:

Disk /dev/hda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1       14592   117210208+   7  HPFS/NTFS
/dev/hda2           14593       14593        8032+  83  Linux

Disk /dev/hdb: 122.9 GB, 122942324736 bytes
255 heads, 63 sectors/track, 14946 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1       14379   115499286   83  Linux
/dev/hdb2           14380       14946     4554427+   f  W95 Ext'd (LBA)
/dev/hdb5           14380       14946     4554396   82  Linux swap / Solaris

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       19457   156288321    7  HPFS/NTFS

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        9729    78148161    7  HPFS/NTFS

Disk /dev/sdc: 30.0 GB, 30005821440 bytes
255 heads, 63 sectors/track, 3648 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1          10       80293+   0  Empty
/dev/sdc2              11        3648    29222235    b  W95 FAT32

Disk /dev/sdh: 203.9 GB, 203928109056 bytes
255 heads, 63 sectors/track, 24792 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdh1   *           1       24792   199141708+   7  HPFS/NTFS

****************************************************************

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hdb1       /               reiserfs notail          0       1
/dev/hdb5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
/dev/sda        /media/usb0     auto    rw,user,noauto  0       0
/dev/sdb        /media/usb1     auto    rw,user,noauto  0       0
/dev/sdc        /media/usb2     auto    rw,user,noauto  0       0

**************************************************************************

Lastly I tried to mount with the following:

mount /dev/sdb

and this is what I received

"mount: I could not determine the filesystem type, and none was specified"

So I specified the file system type with the mount -t command.

PS: I reboot the system and later connected my ipod, so device now shows at sdb instead of sdc when connected earlier.

---

### Post by Sutekh on 2006-02-19
[QUOTE=AdministratorX]
Disk /dev/sdc: 30.0 GB, 30005821440 bytes
255 heads, 63 sectors/track, 3648 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1          10       80293+   0  Empty
**/dev/sdc2              11        3648    29222235    b  W95 FAT32**

[/QUOTE]
If that is the third hard drive then it is not NTFS but **FAT32**

If you wanted to mount it you would need to use
```
sudo mount /dev/**sdc2** /media/usb2/ -t vfat -o iocharset=utf8,umask=000 0 0
```

[QUOTE=AdministratorX]
****************************************************************

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hdb1       /               reiserfs notail          0       1
/dev/hdb5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
/dev/sda        /media/usb0     auto    rw,user,noauto  0       0
/dev/sdb        /media/usb1     auto    rw,user,noauto  0       0
**/dev/sdc        /media/usb2     auto    rw,user,noauto  0       0**

**************************************************************************

[/QUOTE]
This line should be 
```
/dev/sdc2  /media/usb2 vfat iocharset=utf,umask=000 0 0
```

And while I'm at it.  The sda and sdb lines should be like these
```
/dev/sda1 /media/usb0 ntfs nls=utf8,umask=0222 0 0
/dev/sdb1 /media/usb1 ntfs nls=utf8,umask=0222 0 0
```

[QUOTE=AdministratorX]PS: I reboot the system and later connected my ipod, so device now shows at sdb instead of sdc when connected earlier.[/QUOTE]
Ah well I'm battling with this myself and my MP3 player, which seems to change each reboot.

---

### Post by jdmpike on 2006-02-23
Hello all,

I am having a similar problem mounting my usb disk. I can mount the drive with 'sudo mount /dev/sda1 /media/usbdisk -t vfat' but then I don't have permissions to write to it...

Here is the output from the commands you asked earlier...

Output of fdisk -l:

```
remote@jdmlaptop:~$ fdisk -l

Disk /dev/sda: 30.7 GB, 30758289408 bytes
255 heads, 63 sectors/track, 3739 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

```

... and /etc/fstab ...
```

remote@jdmlaptop:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/mapper/Ubuntu-root /               ext3    defaults,errors=remount-ro 0    1
/dev/hda1       /boot           ext3    defaults        0       2
/dev/mapper/Ubuntu-swap_1 none            swap    sw              0       0
/dev/hdb        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

```

This exact disk used to mount automatically when I plugged it in. But its filesystem was NTFS, so I decided to format it as VFAT so it would be usable with real os's.

I would really like to be able to write to it again, so please help sort me out!

---

### Post by Sutekh on 2006-02-23
[QUOTE=jdmpike]
Output of fdisk -l:

```
remote@jdmlaptop:~$ fdisk -l

Disk /dev/sda: 30.7 GB, 30758289408 bytes
255 heads, 63 sectors/track, 3739 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

```
[/QUOTE]
 - There is just a bit missing from this to tell, but I'm gonna take it that *you* know for sure the name of the partition.  

 - It's definately **/dev/sda1**, yes?



[QUOTE=jdmpike]
I can mount the drive with 'sudo mount /dev/sda1 /media/usbdisk -t vfat' but then I don't have permissions to write to it...
[/QUOTE]
 - First create a folder to mount the partition to
```
sudo mkdir **/<mount folder>**
```
 - Then try this command to mount it
```
sudo mount /dev/sda**1** **/<mount folder>** -t vfat -o iocharset=utf8,umask=000 0 0
```
 - I'm assuming that the partition is sda**1**, so make sure that i assumed right!

 - **/<mount folder>** should be changed to the folder where you want to mount the FAT partition.



[QUOTE=jmpike]
... and /etc/fstab ...
```

remote@jdmlaptop:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/mapper/Ubuntu-root /    ext3    defaults,errors=remount-ro 0    1
/dev/hda1       /boot           ext3    defaults        0       2
/dev/mapper/Ubuntu-swap_1 none            swap    sw              0       0
/dev/hdb        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

```

This exact disk used to mount automatically when I plugged it in. But its filesystem was NTFS, so I decided to format it as VFAT so it would be usable with real os's.

I would really like to be able to write to it again, so please help sort me out![/QUOTE]
 - The line you need to add to your /etc/fstab is
```
/dev/sda**1** **/<mount folder>** vfat iocharset=utf8,umask=000 0 0
```
 - Once you've finished adding that line, issue this command
```
sudo mount -a
```
 - Then you are done.

 - This whole process will make the partition mount automatically rather than having to use the **mount** command every time

 - Again make sure that the options in bold are correct for you

---

### Post by jdmpike on 2006-02-24
Thanks very much for that!

It worked like a charm.

Can you tell me a little bit more about what I added to the filesystem table?

I am not sure how umask and iocharset work and need a somewhat less technical explination so I can digest it.

Much love in ubuntu,

Jordan

---

### Post by jdmpike on 2006-02-24
The only problem with this is that it mounts the drive as root and I **STILL** can't write too it as a user...

I have tried to 'sudo chgrp -R users /media/usbdisk', but I don't seem to have perms....

Help ME!

Thanks!

---

### Post by Mustard on 2006-02-24
[QUOTE=jdmpike]The only problem with this is that it mounts the drive as root and I **STILL** can't write too it as a user...

I have tried to 'sudo chgrp -R users /media/usbdisk', but I don't seem to have perms....

Help ME!

Thanks![/QUOTE]

It would be helpful to show the output of these commands so that we can see the current state of your system...

```
cat /etc/fstab
```

```
sudo fdisk -l
```

You may have shown one of them already, but its still important to see what changes you have made since the last time you showed them.

---

### Post by jdmpike on 2006-02-25
I posted this information above, but here it is again.

fdisk -l shows my main disk, plus this guy, /dev/sda1, the one I want to mount with permissions so members of 'users' can right to it.
 
```
Disk /dev/sda: 30.7 GB, 30758289408 bytes
255 heads, 63 sectors/track, 3739 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3738    30025453+   c  W95 FAT32 (LBA)

```

and /etc/fstab looks like this...
```

/dev/sda1       /media/usbdisk  vfat iocharset=utf8,umask=000 0 0

```

When I run mount -a, the usbdisk mounts fine. The problem is that root is the owner and the group. I have tried to 'sudo chgrp -R users /media/usbdisk', but I am not permitted to do so.

Do I simply need to change the entry in /etc/fstab to give it the uid of the 'users' group, so uid=100?

Thanks for the help ubuntu-ers. BTW, I CAN"T WAIT FOR DAPPER!!!

Peace, love, and ubuntu,

Jordan

---

### Post by Mustard on 2006-02-25
The problem is the way you have it set up currently should be working.  What you have in your /etc/fstab line is exactly what is needed to allow users to access the contents of that partition.  So that makes it pretty hard to advise you on what to do, since you have done it already.  Something is amiss though, its just that I can't see what is wrong from the information given.

Have you rebooted since making those changes?

What you are saying concerning the folder being owned by root is really not the problem.  I have my windows drive mounted on /media/windows with the same fstab line basically.

```
/dev/hdb1       /media/windows  vfat    iocharset=utf8,umask=000  0    0

```

and this is what ls -al shows when run in my /media folder...

```
drwxrwxrwx   6 root    root     8192 1970-01-01 10:00 windows

```

I can read and write to that drive even though the folder is owned by root.

With regards to 'uid', uid is the user id.  gid is the group id.  A command I used to use to manually mount my USB drive and only give my user permission to access it was this...

```
sudo mount -t vfat /dev/sda1 /media/usbdrive -o user,uid=1000,gid=1000
```

Reading through the manual for mount, the 'user' option allows a user to mount the device, whereas the 'users' option would all users to mount the device.  The uid and gid of 1000 refer to my specific user and group id.

---

### Post by Sutekh on 2006-02-25
> **jdmpike]
I am not sure how umask and iocharset work and need a somewhat less technical explination so I can digest it.
[/QUOTE]
Don't know if this is less technical but I'll try.

**iocharset=utf8** allows reading of the UTF8 Unicode character set.  I think this applies to files with longer file names.

**umask** is a number representing the level of permissions.  It works by *removing* permissions from full access. There are three parameters that are each represented by a number. Each number corresponds to a level of access said:**
> 
umask: octal file permissions

You can change permissions using the parameter umask. But be aware that it must be the bitmask of permissions that are not present for the mountpoint. It is an octal number, formed like this:

* character '0': Indicates that this is an octal number, not decimal.
* first digit: owner user permissions
* second digit: owner group permissions
* third digit: world permissions (every other user on the system)

The modes are as follows (the first column is the mode octal number):

M | R W X
-------------
0 | * * *
1 | * * -
2 | * - *
3 | * - -
4 | - * *
5 | - * -
6 | - - *
7 | - - -

For example, if you want that everybody be able to read, write, and execute every file in your /mnt/c, you should specify the mask 0000: 
Or if you used a **umask=0543** (just to be completely random), it would have write access for the owner, write and execute access for the group owner, and read access for everyone else.




Getting back to your current problem.

Here is the output of **sudo fdisk -l** concerning my FAT32 partition
```
Disk /dev/hda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               1       14593   117218241    5  Extended
/dev/hda5               1       14593   117218209+   b  W95 FAT32

```

Here is the mount line in my /etc/fstab for said partition
```

/dev/hda5 /mnt/os-shared vfat iocharset=utf8,umask=0000 0 0

```

Here is the listing of the /mnt directory, when I run **ls -l**
```
d**rwxrwxrwx**  6 root root       65536 1970-01-01 10:00 os-shared

```
Like **Mustard**, my FAT32 partition, mounted in /mnt/os-shared is owned by root.  However it allows full permissions, as seen from the letters on the left.  The **rwxrwxrwx** corresponds to read/write/execute permissions for owner/group owner/everyone else.

Finally here is my normal user trying to create a folder in the FAT32 partition
```
user@ubuntu:/mnt/os-shared$ mkdir test
user@ubuntu:/mnt/os-shared$ ls -l
...
drwxrwxrwx  2 root root     65536 2006-02-26 11:47 test
...
user@ubuntu:/mnt/os-shared$

```
So even though **root** owns the mount folder (and all files underneath) I (as a normal user) still have the ability to create folders and files.  

Perhaps you could check that your mount folder has the same level or permissions with
```
ls -l /media/
```

Otherwise I'm really confused, because everything else looks okay.

---

### Post by Mohd Hafiz on 2006-02-25
Hi,
I have similar but not same problem,
sorry, i have move my post here [http://ubuntuforums.org/showthread.php?p=771227#post771227](http://ubuntuforums.org/showthread.php?p=771227#post771227)

---

### Post by unperson on 2006-02-25
[QUOTE=jdmpike]
and /etc/fstab looks like this...
```

/dev/sda1       /media/usbdisk  vfat iocharset=utf8,umask=000 0 0

```

When I run mount -a, the usbdisk mounts fine. The problem is that root is the owner and the group. I have tried to 'sudo chgrp -R users /media/usbdisk', but I am not permitted to do so.

Do I simply need to change the entry in /etc/fstab to give it the uid of the 'users' group, so uid=100?

Thanks for the help ubuntu-ers. BTW, I CAN"T WAIT FOR DAPPER!!!

Peace, love, and ubuntu,

Jordan[/QUOTE]

I can't say for sure what is going on, but I think this info may help.  From the "Mount options for FAT" section of the mount man page:

> 
uid=value and gid=value
Set the owner and group of all files.  (Default: the uid and gid of the current process.)


The issue is that unlike UNIX type filesystems, a FAT partition doesn't have information in it about who owns all the files, so the system has to arbitrarily assign an owner when you mount it.  By default it assigns the owner to be whoever ran the mount command.  If you run mount under sudo, that user will be root (I think).  I believe this is why "sudo mount -a" is causing it to be mounted with root as the owner.  If you had an entry in /etc/fstab with the "user" or "users" option set, then an ordinary user could use the mount command to mount that filesystem without sudo.  In that case, the user who used the mount command would be set as the owner.

On the other hand, you can specify the user ID and group ID for the files in filesystem using the uid= and gid= options for mount (or in /etc/fstab) to set a certain user (and group) as owner of the files when the filesystem is mounted.  You would do this by adding uid=1001,gid=1010 to the options (after -o in the mount command) to, for example, make user ID 1001 the owner (and group ID 1010).  In that case, the user with UID 1001 could write to any of the files that had user write permission set, and anyone in the group with GID 1010 could write to any files that had group write permission set.

When hotpluggable stuff it automounted I'm not sure exactly how the owner of the files is determined.  I'm guessing ownership is assigned to whoever is running the desktop (if anyone).  That's how it *seems* to work, but I'm not sure of the details.

Hope that helps.

---

### Post by jdmpike on 2006-02-26
What I don't understand is when I insert a USB jump drive or anything else, I am able to write to it.

It is only my stupid hard drive that has these silly permissions and doesn't mount automatically with no entires into /etc/fstab like other USB devices.

I mount tons of other things like SD Cards, thumb drives, ipod... but this USB drive that has my media on it is the death of me...

Desparately seeking help...

Jordan

---

### Post by jdmpike on 2006-02-26
I seem to have made it work by specifying the gid=100 and the uid=1000, I haven't added a line to /etc/fstab because the device changes names based on what's plugged in at reboot.

Is there a way to specify what devices get what names by some sort of hardware identifier?

Thanks for the help all,

Jordan

---

### Post by barthel on 2006-02-26
[B]I ran into a similar issue with my Western Digital WD 880BB when I switched from Slackware-current to Breezy 3 days ago. Unfortunately, forum login problems kept me from posting until today. Here's the post I intended to make then:
[/B]
Interestingly enough, I also have a Western Digital 800BB that is not automounting correctly.

Background:

This is a fresh install of 5.10. During the install, the USB drives were correctly identified for the initial /etc/fstab.

Because the drives are connected via a PCMCIA card (to provide USB 2.0 on an older laptop), the entries were commented out of /etc/fstab since the devices cannot be mounted until PCMCIA services are running.

The USB drive which is correctly automounted (/dev/sdb) has 2 partitions: NTFS & ext3. The WD 800BB (/dev/sda) has only 1, an ext3.

***** Output of fdisk -l :

```
Disk /dev/hda: 100.0 GB, 100030242816 bytes
255 heads, 63 sectors/track, 12161 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           2           7       48195   84  OS/2 hidden C: drive
/dev/hda2               8        1874    14996677+   7  HPFS/NTFS
/dev/hda3            1875        2870     8000370   83  Linux
/dev/hda4            2871       12161    74629957+   5  Extended
/dev/hda5            2871        4862    16000708+  83  Linux
/dev/hda6            4863       12005    57376116   83  Linux
/dev/hda7           12006       12161     1253038+  82  Linux swap / Solaris

Disk /dev/sdb: 20.0 GB, 20003880960 bytes
255 heads, 63 sectors/track, 2432 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        1216     9767488+   7  HPFS/NTFS
/dev/sdb2            1217        2432     9767520   83  Linux

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        9729    78148161   83  Linux


```***** End of fdisk -l output

When attempting to automount the WD 800BB, the following errors appear

***** Output of dmesg | tail:
```
[ 5978.110970] SCSI device sda: 156301488 512-byte hdwr sectors (80026 MB)
[ 5978.110990] sda: assuming drive cache: write through
[ 5978.111007]  /dev/scsi/host3/bus0/target0/lun0: p1
[ 5978.134766] Attached scsi disk sda at scsi3, channel 0, id 0, lun 0
[ 5978.141007] usb-storage: device scan complete
[ 5981.894255] FAT: utf8 is not a recommended IO charset for FAT filesystems, filesystem will be case sensitive!
[ 5981.898632] FAT: Did not find valid FSINFO signature.
[ 5981.898641]      Found signature1 0x00000000 signature2 0x00000000 (sector = 1)
[ 5981.899300] FAT: Filesystem panic (dev sda1)
[ 5981.899312]     invalid access to FAT (entry 0x00c00008)
[ 5981.899318]     File system has been set read-only


```***** End of dmesg output

Yes, for som reason, dbus/hal/gnome-volume-manager are seeing this partition as FAT/VFAT, not ext3

***** Relevant output from lshal:
```
udi = '/org/freedesktop/Hal/devices/volume_uuid_15E7_2925'
  volume.policy.desired_mount_point = 'WDC USB2'  (string)
  volume.policy.mount_filesystem = 'vfat'  (string)
  volume.policy.should_mount = true  (bool)
  info.udi = '/org/freedesktop/Hal/devices/volume_uuid_15E7_2925'  (string)
  info.product = 'WDC USB2'  (string)
  volume.size = 80023716864  (0x12a1c90400)  (uint64)
  volume.num_blocks = 156296322  (0x950e482)  (int)
  volume.block_size = 512  (0x200)  (int)
  volume.partition.number = 1  (0x1)  (int)
  info.capabilities = {'volume', 'block'} (string list)
  info.category = 'volume'  (string)
  volume.is_partition = true  (bool)
  volume.is_disc = false  (bool)
  volume.is_mounted = false  (bool)
  volume.mount_point = ''  (string)
  volume.label = 'WDC USB2'  (string)
  volume.uuid = '15E7-2925'  (string)
  volume.fsversion = 'FAT32'  (string)
  volume.fsusage = 'filesystem'  (string)
  volume.fstype = 'vfat'  (string)
  block.storage_device = '/org/freedesktop/Hal/devices/storage_model_WD800BB_00DKA0'  (string)
  block.is_volume = true  (bool)
  block.minor = 1  (0x1)  (int)
  block.major = 8  (0x8)  (int)
  block.device = '/dev/sda1'  (string)
  linux.hotplug_type = 3  (0x3)  (int)
  info.parent = '/org/freedesktop/Hal/devices/storage_model_WD800BB_00DKA0'  (string)
  linux.sysfs_path_device = '/sys/block/sda/sda1'  (string)
  linux.sysfs_path = '/sys/block/sda/sda1'  (string)


```***** End of lshal output

Basically, I have no idea where the 'WDC USB2' label and 'vfat' fstype values are coming from.

I can manually mount the drive, but automounting fails every time.

While I can add custom udev rules to handle this correctly (I had them for Slackware-current), it would require disabling the automount functionality entirely--if only for consistency with all my devices.

I'd appreciate any pointers--even if only how to categorize a bug report.

Thanks!

**Additional followup, for what it's worth:**

I still can't get the automounter to properly recognize the WD drive.

HOWEVER, I did discover that when I unmounted one partition of the other drive via Nautilus, the other partition was also unmounted at the same time. (When I manually mounted them, only the selected partition was mounted.)

Taking that into consideration with the fact that the label of the WD drive is taken from the base device instead of the partition, I've come to the conclusion that some aspect of the system is looking at the partition table only to determine how many partitions to mount--and because my WD drive has only 1 partition, for some reason the MBR is being used to determine that it's a VFAT partition, even though the partition table correctly identifies is as ext3.

At this point, my solution has to be writing custom udev rules because I need persistently named symlinks and because the automounter does not perform an fsck when mounting the drives. This is what I had done under Slackware, so it's not a big issue for me. I had even gone so far as to completely disable HAL because I hated the way it was modifying my /etc/fstab and creating entries for already mounted devices. While I'm glad to see that HAL no longer has that particular annoying feature, the truth is that I'm not familiar enough with the entire subsystem to identify which piece is at fault. Unless this is already fixed in Dapper, I'd like to file an appropriate bug report.

So.... Can anyone tell me if the culprit is DBUS, HAL, UDEV, or GNOME Volume Manager? 

Thanks (and my apologies for the lengthy post.)

P.S. So far, I'v VERY happy with Ubuntu and am glad I've made the switch. (I've been a Slacker since the 1.2 kernel series... :cool: )

---

