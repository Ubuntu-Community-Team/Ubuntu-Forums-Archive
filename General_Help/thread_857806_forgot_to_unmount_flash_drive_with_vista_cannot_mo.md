---
title: "forgot to unmount flash drive with vista cannot mount now"
date: 2008-07-12
forum: General Help
---

### Post by jasonpeinko on 2008-07-12
I was getting rid of vista on my moms laptop and put some files to backup on a flash drive, and reformatted. But i forgot to unmount the drive!

so now it will not mount in ubuntu or xp is there a way to get it to mount? 

if i plug it in a vista computer will it work?

---

### Post by Dr Small on 2008-07-12
If all else fails, simply reformat the drive. I have had this happen to me several times between XP and Ubuntu, and ended up having to reformat to FAT32 or something. (I Forget what FS it is).

Dr Small

---

### Post by cdtech on 2008-07-12
Just run "ntfsfix" on the device, you should be ok.

Hope this helps.........

---

### Post by dcstar on 2008-07-12
> **jasonpeinko said:**
> I was getting rid of vista on my moms laptop and put some files to backup on a flash drive, and reformatted. But i forgot to unmount the drive!

so now it will not mount in ubuntu or xp is there a way to get it to mount? 

if i plug it in a vista computer will it work?

Install the **ntfsprogs** package, and then in a terminal:

```
fsck /dev/whateveryourusbis
```

---

### Post by jasonpeinko on 2008-07-12
will this delete the data?

---

### Post by boblemur on 2008-07-12
you could try force mounting it in ubuntu and then unmounting it...
```

sudo mkdir /mnt/usb
sudo mount /dev/?? /mnt/usb -t ntfs-3g -o force

sudo umount /dev/??
```

this may help... but then again it may not...

---

### Post by jasonpeinko on 2008-07-12
ntfsfix
```

jason@jason:/dev$ sudo ntfsfix usbdev2.14_ep00
Mounting volume... Error opening partition device: No such device or address.
Failed to startup volume: No such device or address.
FAILED
Attempting to correct errors... Error opening partition device: No such device or address.
FAILED
Failed to startup volume: No such device or address.
Volume is corrupt. You should run chkdsk.


```

fsck
```

jason@jason:/dev$ sudo fsck /dev/usbdev2.14_ep00
fsck 1.40.8 (13-Mar-2008)
e2fsck 1.40.8 (13-Mar-2008)
fsck.ext2: No such device or address while trying to open /dev/usbdev2.14_ep00
Possibly non-existent or swap device?


```

mount 
```

jason@jason:/dev$ sudo mount /dev/usbdev2.14_ep00 -t ntfs-3g -o force
Usage: mount -V                 : print version
       mount -h                 : print this help
       mount                    : list mounted filesystems
       mount -l                 : idem, including volume labels
So far the informational part. Next the mounting.
The command is `mount [-t fstype] something somewhere'.
Details found in /etc/fstab may be omitted.
       mount -a [-t|-O] ...     : mount all stuff from /etc/fstab
       mount device             : mount device at the known place
       mount directory          : mount known device here
       mount -t type dev dir    : ordinary mount command
Note that one does not really mount a device, one mounts
a filesystem (of the given type) found on the device.
One can also mount an already visible directory tree elsewhere:
       mount --bind olddir newdir
or move a subtree:
       mount --move olddir newdir
One can change the type of mount containing the directory dir:
       mount --make-shared dir
       mount --make-slave dir
       mount --make-private dir
       mount --make-unbindable dir
One can change the type of all the mounts in a mount subtree
containing the directory dir:
       mount --make-rshared dir
       mount --make-rslave dir
       mount --make-rprivate dir
       mount --make-runbindable dir
A device can be given by name, say /dev/hda1 or /dev/cdrom,
or by label, using  -L label  or by uuid, using  -U uuid .
Other options: [-nfFrsvw] [-o options] [-p passwdfd].
For many more details, say  man 8 mount .


```

---

### Post by boblemur on 2008-07-12
sudo mount /dev/?? /mnt/usb -t ntfs-3g -o force


you have missed the second location... where you want to mount it to...

check that it appears in fdisk...

sudo fdisk -l | grep '/dev/'

---

### Post by jasonpeinko on 2008-07-12
```

jason@jason:~$ sudo mount /dev/usbdev2.14_ep00 /mnt/usb -t ntfs-3g -o force
Error opening partition device: No such device or address
Failed to mount '/dev/usbdev2.14_ep00': No such device or address
You seem to have a SoftRAID/FakeRAID hardware and must use an activated,
different device under /dev/mapper/, (e.g. /dev/mapper/nvidia_eahaabcc1)
to mount NTFS. Please see the 'dmraid' documentation for help.
jason@jason:~$ sudo fdisk -l | grep '/dev/'
Disk /dev/sda: 80.0 GB, 80026361856 bytes
/dev/sda1   *           1        9327    74919096   83  Linux
/dev/sda2            9328        9729     3229065    5  Extended
/dev/sda5            9328        9729     3229033+  82  Linux swap / Solaris
Disk /dev/sdb: 4294 MB, 4294967296 bytes
jason@jason:~$ sudo mount /dev/sdb /mnt/usb -t ntfs-3g -o force
NTFS signature is missing.
Failed to mount '/dev/sdb': Invalid argument
The device '/dev/sdb' doesn't have a valid NTFS.
Maybe you selected the wrong device? Or the whole disk instead of a
partition (e.g. /dev/hda, not /dev/hda1)? Or the other way around?
jason@jason:~$ ntfsfix /dev/sdb
Mounting volume... Error opening partition device: Permission denied.
Failed to startup volume: Permission denied.
FAILED
Attempting to correct errors... Error opening partition device: Permission denied.
FAILED
Failed to startup volume: Permission denied.
Volume is corrupt. You should run chkdsk.
jason@jason:~$ sudo ntfsfix /dev/sdb
Mounting volume... Failed to startup volume: Invalid argument.
FAILED
Attempting to correct errors... FAILED
Failed to startup volume: Invalid argument.
Volume is corrupt. You should run chkdsk.
jason@jason:~$ fsck /dev/sdb
fsck 1.40.8 (13-Mar-2008)
e2fsck 1.40.8 (13-Mar-2008)
fsck.ext2: Permission denied while trying to open /dev/sdb
You must have r/w access to the filesystem or be root
jason@jason:~$ sudo fsck /dev/sdb
fsck 1.40.8 (13-Mar-2008)
e2fsck 1.40.8 (13-Mar-2008)
fsck.ext2: Superblock invalid, trying backup blocks...
fsck.ext2: Bad magic number in super-block while trying to open /dev/sdb

The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>



```

---

### Post by boblemur on 2008-07-12
i had a similar problem... are you sure its not a fat parition on the usb stick??


try:

sudo mount /dev/sdb /mnt/usb -t vfat

that worked for me...maybe not for you though...

---

### Post by jasonpeinko on 2008-07-13
```

mount: wrong fs type, bad option, bad superblock on /dev/sdb,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so


```

I apperciate the fast responses guys.

---

### Post by boblemur on 2008-07-13
ummmm im not really sure what you should try next...but your parition is not showing up in fstab so the computer dosent recognise it


you could look in gparted and see what it sees... it may recognise the partition
```

sudo apt-get gparted
```

---

### Post by jasonpeinko on 2008-07-13
in gparted it shows up as unallocated so does this mean my stuff is gone?

---

### Post by boblemur on 2008-07-13
it could do... however your stuff will still be there...

because nothing has over writen it... it seems as though you are mearly missing the dos tag and some parition information the disk...

but the files themselves will still be there... how you should get to them im not sure... just dont reformat it just yet because their may be a way to repair the partition table...

---

### Post by cdtech on 2008-07-13
"ntfsfix" will not erase your data.

---

### Post by jasonpeinko on 2008-07-13
jason@jason:~$ sudo ntfsfix /dev/sdb
Mounting volume... Failed to startup volume: Invalid argument.
FAILED
Attempting to correct errors... FAILED
Failed to startup volume: Invalid argument.
Volume is corrupt. You should run chkdsk.
jason@jason:~$

---

### Post by dcstar on 2008-07-13
> **jasonpeinko said:**
> jason@jason:~$ sudo ntfsfix /dev/sdb
Mounting volume... Failed to startup volume: Invalid argument.
FAILED
Attempting to correct errors... FAILED
Failed to startup volume: Invalid argument.
Volume is corrupt. You should run chkdsk.
jason@jason:~$

/dev/sdb is a device - /dev/sdb1 is a partition, you run the program on partitions.

---

### Post by boblemur on 2008-07-13
have you tried running chkdsk under windows?? it may fix it...

also im not sure if fdisk could remake the partition table without actually formatting the drive... and then ntfs fix may work... but that would be a last resort cause fdisk may accidently format it..

---

### Post by jasonpeinko on 2008-07-13
```

jason@jason:~$ sudo ntfsfix /dev/sdb1
Failed to determine whether /dev/sdb1 is mounted: No such file or directory.
Mounting volume... Error opening partition device: No such file or directory.
Failed to startup volume: No such file or directory.
FAILED
Attempting to correct errors... Error opening partition device: No such file or directory.
FAILED
Failed to startup volume: No such file or directory.
Volume is corrupt. You should run chkdsk.


```
according to gparted there is no partitions

---

### Post by cdtech on 2008-07-13
First you need to find your device using "sudo fdisk -l" then run the command on the USB device listed....

---

### Post by jasonpeinko on 2008-07-13
> **boblemur said:**
> have you tried running chkdsk under windows?? it may fix it...

also im not sure if fdisk could remake the partition table without actually formatting the drive... and then ntfs fix may work... but that would be a last resort cause fdisk may accidently format it..

```

The type of the file system is RAW
CHKDSK is not available for RAW drives.

```

---

### Post by jasonpeinko on 2008-07-13
> **cdtech said:**
> First you need to find your device using "sudo fdisk -l" then run the command on the USB device listed....



jason@jason:~$ sudo fdisk -l

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0006e7b4

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9327    74919096   83  Linux
/dev/sda2            9328        9729     3229065    5  Extended
/dev/sda5            9328        9729     3229033+  82  Linux swap / Solaris

Disk /dev/sdb: 4294 MB, 4294967296 bytes
133 heads, 62 sectors/track, 1017 cylinders
Units = cylinders of 8246 * 512 = 4221952 bytes
Disk identifier: 0x00000001

   Device Boot      Start         End      Blocks   Id  System

---

### Post by boblemur on 2008-07-13
hes already posted his fdisk... and his usb does not have a partition recognized because the partition table is corrupt/mia so he cant mount the partition to use ntfsfix the thing i was thinking...

is maybe get fdisk to try and rewrite the partitions that were there and then see if you can mount them....

---

### Post by cdtech on 2008-07-13
I see sdb as a USB stick, is that right?

---

### Post by dcstar on 2008-07-13
> **jasonpeinko said:**
> I was getting rid of vista on my moms laptop and put some files to backup on a flash drive, and reformatted. But i forgot to unmount the drive!
.........

Well, after all the rest you have posted you seem to have lost any and all data on the drive - which isn't surprising given the circumstances.

Call it a day and reformat the USB.

---

### Post by boblemur on 2008-07-13
Disk /dev/sdb: 4294 MB, 4294967296 bytes
133 heads, 62 sectors/track, 1017 cylinders
Units = cylinders of 8246 * 512 = 4221952 bytes
Disk identifier: 0x00000001

Device Boot Start End Blocks Id System

yes thats what i would guess but it DOSENT HAVE ANY PARTITIONS

---

### Post by jasonpeinko on 2008-07-13
technically is a zen vision w in removable disk mode.

Im just going to give up, and reformat it seems like a hopeless battle

---

### Post by cdtech on 2008-07-13
Before you format just try /dev/sdb1 and see what it say's.....

---

### Post by jasonpeinko on 2008-07-13
jason@jason:~$ sudo ntfsfix /dev/sdb1
Failed to determine whether /dev/sdb1 is mounted: No such file or directory.
Mounting volume... Error opening partition device: No such file or directory.
Failed to startup volume: No such file or directory.
FAILED
Attempting to correct errors... Error opening partition device: No such file or directory.
FAILED
Failed to startup volume: No such file or directory.
Volume is corrupt. You should run chkdsk.

---

### Post by boblemur on 2008-07-13
please try

sudo fdisk /dev/sdb 

then press

o and enter
n and select ntfs-3g and make it the entire disk then
w and enter and see if that works (may format it anyways)

---

### Post by jasonpeinko on 2008-07-13
no i just formatted it

---

