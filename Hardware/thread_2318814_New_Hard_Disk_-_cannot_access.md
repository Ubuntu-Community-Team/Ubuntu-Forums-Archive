---
title: "New Hard Disk - cannot access"
date: 2016-03-29
forum: Hardware
---

### Post by Boris786 on 2016-03-29
Hello,

O/S = Ubuntu 14.04 LTS dual booting currently with Windows 7.

I have seen several posts which are close to answering this - they may in fact do so but I would like to be sure.

I have an additional hard disk in my laptop. This was previously formatted as NTFS. I have now made Ext 4 using Gparted (320 gb hard drive - ext partition = 298.9 Gb). Not sure what the other 4 gb used for.

I cannot access this disk from within Ubuntu but it does seem to be mounted. Could you advise on how to resolve? This all began as I want to use this disk for steam library within Ubuntu and I do not think you can if NTFS.

I would also like to name or label it. 

Paul

---

### Post by Bashing-om on 2016-03-29
Boris786; Hello ;

Installed that hard drive internally ? Then you have to make the system aware of its existence - 
as the system will not dictate how you use it . You must advise the system what you want to do .
Either manually mounting the file system
Or automounting the file system(s) via the FSTABle file .

show us what you are working with:
```

sudo fdisk -lu ##for the legacy partitioning scheme
sudo parted -l

```
once the hard drive identification is known we can discuss how you want to mount the related files system. 

[INDENT][INDENT]really
[INDENT]it ain't nothing but a thing[/INDENT][/INDENT][/INDENT]

---

### Post by Boris786 on 2016-03-29
Thanks please see below.[B] 

sudo fdisk -lu =[/B]

psas@psas-Bonobo-Extreme:~$ sudo fdisk -lu
[sudo] password for psas: 

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00088b4d

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048      206847      102400    7  HPFS/NTFS/exFAT
/dev/sda2          206848    97863097    48828125    7  HPFS/NTFS/exFAT
/dev/sda3        97863680    98840575      488448   83  Linux
/dev/sda4        98842622   234440703    67799041    5  Extended
/dev/sda5        98842624   157433855    29295616   83  Linux
/dev/sda6       157435904   234440703    38502400   83  Linux

Disk /dev/sdb: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x00005527

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1            2048   625141759   312569856   83  Linux

Disk /dev/sdc: 2004 MB, 2004877312 bytes
62 heads, 62 sectors/track, 1018 cylinders, total 3915776 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0004a544

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *          62     3913191     1956565    6  FAT16
psas@psas-Bonobo-Extreme:~$ 

**sudo parted -l =**

psas@psas-Bonobo-Extreme:~$ sudo parted -l
Model: ATA INTEL SSDSC2CW12 (scsi)
Disk /dev/sda: 120GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type      File system  Flags
 1      1049kB  106MB   105MB   primary   ntfs         boot
 2      106MB   50.1GB  50.0GB  primary   ntfs
 3      50.1GB  50.6GB  500MB   primary   ext4
 4      50.6GB  120GB   69.4GB  extended
 5      50.6GB  80.6GB  30.0GB  logical   ext4
 6      80.6GB  120GB   39.4GB  logical   ext4


Model: ATA ST320LM001 HN-M3 (scsi)
Disk /dev/sdb: 320GB
Sector size (logical/physical): 512B/4096B
Partition Table: msdos

Number  Start   End    Size   Type     File system  Flags
 1      1049kB  320GB  320GB  primary  ext4


Model: Generic Flash Disk (scsi)
Disk /dev/sdc: 2005MB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
 1      31.7kB  2004MB  2004MB  primary  fat16        boot

---

### Post by Boris786 on 2016-03-29
Oh I should say I am away to work shortly and will return to this tom late afternoon. Thanks for your help so far.

---

### Post by Bashing-om on 2016-03-29
Boris786; K;

As you do not say;
I take for granted that;
sda is the system install
sdb is the backup drive - single partition
sdc is a liveUSB

Our focus is that 2nd hard drive, sdb.
What now results:
```

sudo mkdir /mnt/backup
sudo mount /dev/sdb1 /mnt/backup
ls -al /mnt/backup

```
when all done looking and checking .. as "you" mounted that file system it is on you to un-mount it. Failure to remember to UNmount can result in file system corruption !
```

sudo umount /mnt/backup

```

OK, you like what you see .. do you want to have control on when that backup drive is mounted OR do you want it available upon the system booting for all to have access to this hard drive ?
[http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131) <- bodhi.zazen -Understanding fstab
[http://ubuntuforums.org/showthread.php?t=1983336](http://ubuntuforums.org/showthread.php?t=1983336)
[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)

[INDENT][INDENT]it is your system
[INDENT][INDENT][INDENT]do it your way
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by Boris786 on 2016-03-31
You are correct. Well had go and failed. When restarting fails and I have to skip disk. I am not sure what I am doing but I think I am creating mount point and then referencing that in fstab. Or rather failing to.
Incidentally can partitions in Ext4 be used by windows?
I am thinking you might want to see fstab:

# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda5 during installation
UUID=22c12bf3-7d99-4988-882d-25dcf609bc9f /               ext4    errors=remount-ro 0       1
# /boot was on /dev/sda3 during installation
UUID=25f3d659-a0df-4573-b6f1-b5c7979a3795 /boot           ext4    defaults        0       2
# /home was on /dev/sda6 during installation
UUID=6b354f2b-dc2e-44df-beb7-4e4f9fbbee7a /home           ext4    defaults        0       2
/dev/disk/by-uuid/87fb44fc-544e-406d-a36a-9fb9801caa4e /home/psas/Mount ext4 nosuid,nodev,nofail,x-gvfs-show 0 0

I rely on your good will and patience.

---

### Post by Boris786 on 2016-03-31
Oh when restarting the failure message is 'an error ocurred when mounting /home/psas/mount. The mount point I tried to create is /home/psas/mount/HD2

---

### Post by Boris786 on 2016-03-31
Sorry further info when accessing within home:Error mounting system-managed device /dev/sdb1: Command-line `mount "/home/psas/Mount"' exited with non-zero exit status 32: mount: wrong fs type, bad option, bad superblock on /dev/sdb1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

---

### Post by Boris786 on 2016-03-31
OK last post fpr today. If I reformat as FAT32 I can use although when booting I have to 'skip' as disk is 'not ready'. I do not understand what is going on. anything to do with partition table being MSDOS?
Model: ATA ST320LM001 HN-M3 (scsi)
Disk /dev/sdb: 320GB
Sector size (logical/physical): 512B/4096B
Partition Table: msdos

---

### Post by Bashing-om on 2016-03-31
Boris786; Oh Boy ...

What a mess we have created.
IRT:
> 
Incidentally can partitions in Ext4 be used by windows?

No, not with out help. To Windows there is no other operating system in the world. Unlike linux .

As you have made changes. let us see an updated status:
show:
```

sudo fdisk -lu
sudo blkid
cat /etc/fstab

```
You want your /home mount point to be of a similarity:
```

# /home was on /dev/sda2 during installation
UUID=29a6fc4f-ff12-4cac-8eb1-e98e50f1107f /home           ext4    defaults        0       2

```
Where the UUIDs and mount points must be valid and correct. Else you drive the system nuts.

also; " If I reformat as FAT32 "  , there is a 4GB limit on files being stored . For a storage device, not a good option. If you are to share this storage device with Windows .. NTFS is the better choice. If totally devoted to ubuntu make the file system format as 'ext4' .

[INDENT][INDENT]which way did he go, George
[/INDENT][/INDENT]

---

### Post by Boris786 on 2016-03-31
Sorry in desperation. I needed to have an operational disk so I reformatted as FAT. This works in the sense that I can access additional disk and use material on it.
To take a step backwards, I began with an NTFS formatted disk and this was working fine. I then after an internet trawl thought I should reformat as Ext4 to allow me to Steam library to this disk.
Rather irritatingly and I hold myself responsible for this I now think my better option is to revert back to NTFS and then get this to work as steam library.
If this is not an option and Ext4 is the way to go I could lose windows and go entirely Linux but would prefer NTFS route.

I think what I need to do is:

1. Format additional hard drive (Sdb) to NTFS.
2. Set up mount point for this.
3. Preferable name folder (I am thinking this is done under 2)
4. Set permissions for steam folder on Sdb to run executables.

I am assuming that I do this in the order above. I am assuming this is as 'simple' as doing the above properly:

Sorry for the hassle. Where I am now (bit weary)

**Sudo fdisk lu:**

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00088b4d

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048      206847      102400    7  HPFS/NTFS/exFAT
/dev/sda2          206848    97863097    48828125    7  HPFS/NTFS/exFAT
/dev/sda3        97863680    98840575      488448   83  Linux
/dev/sda4        98842622   234440703    67799041    5  Extended
/dev/sda5        98842624   157433855    29295616   83  Linux
/dev/sda6       157435904   234440703    38502400   83  Linux

Disk /dev/sdb: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x00005527

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1            2048   625141759   312569856    b  W95 FAT32

psas@psas-Bonobo-Extreme:~**$ sudo blkid**
/dev/sda1: LABEL="System Reserved" UUID="8C20C33E20C32DD0" TYPE="ntfs" 
/dev/sda2: UUID="1AA6C50EA6C4EAF9" TYPE="ntfs" 
/dev/sda3: UUID="25f3d659-a0df-4573-b6f1-b5c7979a3795" TYPE="ext4" 
/dev/sda5: UUID="22c12bf3-7d99-4988-882d-25dcf609bc9f" TYPE="ext4" 
/dev/sda6: UUID="6b354f2b-dc2e-44df-beb7-4e4f9fbbee7a" TYPE="ext4" 
/dev/sdb1: UUID="CC36-F3A4" TYPE="vfat" 
psas@psas-Bonobo-Extreme:~**$ cat /etc/fstab**
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda5 during installation
UUID=22c12bf3-7d99-4988-882d-25dcf609bc9f /               ext4    errors=remount-ro 0       1
# /boot was on /dev/sda3 during installation
UUID=25f3d659-a0df-4573-b6f1-b5c7979a3795 /boot           ext4    defaults        0       2
# /home was on /dev/sda6 during installation
UUID=6b354f2b-dc2e-44df-beb7-4e4f9fbbee7a /home           ext4    defaults        0       2
/dev/disk/by-uuid/87fb44fc-544e-406d-a36a-9fb9801caa4e /home/psas/Mount ext4 nosuid,nodev,nofail,x-gvfs-show 0 0

---

### Post by Bashing-om on 2016-03-31
Boris786; Well ...

In your /etc/fstab file, while /root /boot and /home are correct .. the UUID " 87fb44fc-544e-406d-a36a-9fb9801caa4e " no longer exist on your system.
remove :
" /dev/disk/by-uuid/87fb44fc-544e-406d-a36a-9fb9801caa4e /home/psas/Mount ext4 nosuid,nodev,nofail,x-gvfs-show 0 0 "
from the config file .
save the file once the edit has been made.

Is the system happy now ?
```

sudo mount -a

```
You should get only a return to prompt unless the system finds a problem.

Once we have the system stable .. and you have reformatted the drive as NTFS - if that is your choice - then we manually mount the new drive from terminal to know it is in good shape.

then and only then do we edit /etc/fstab once more to automount that added hard drive.

It ain't no big deal. But them 7 Ps apply .
[INDENT][INDENT]Prior Prudent Planning Preventing Pi** Poor Performance
[/INDENT][/INDENT]

---

### Post by Boris786 on 2016-04-01
Yes thanks that makes sense. FStab edited and the system seems to be happy now.
From internet research there seems to be software that helps windows to work with Ext4 but I do not want to learn about windows so on that basis I will go NTFS. I am not quite ready to go full Ubuntu/Linux yet.
So drive now formatted as NTFS and all seems well. sudo mount -a returns to prompt so passes that test.
Next baby step is to manually mount new drive from terminal or have I done this with sudo mount -a?

---

### Post by Bashing-om on 2016-04-01
Boris786; Good deal .

You are making good progress. Yeah, the next step is to manually mount the storage device.
In terminal execute:
a)
```

sudo mkdir /mnt/storage

```
where we make a point ( mount) to attach this external file system to the existing file system. The "mount point" is arbitrary and can be where ever you want . But, there are relational aspects. Say you mount it in /media/<username>, then the GVFS file system is aware and you then have access to the device from the GUI ( file manager). Maybe you want this capability maybe you do not . You make this choice. Os maybe you want it very restrictive to you and root only .. By mounting in your /home then no one else has access to this device. 
b)
```

sudo fdisk -lu

```
where we identify the target device(s) we want to 'attach'.
c)
Let's say the 'fdisk' command identifies our target device as 'sdb' and that there is but the one partition on this device ( that could have many partitions) . That single partition is seen as sdb1 for our tutorial reference.
d)
```

mount -t ntfs /dev/sdb1 /mnt/storage -o "umask=022"

```
where we tell the system explicitly a NTFS file system, where, and with what access rights . Later on you will learn that NTFS ( Windows) is not POSIX compliant and we must set these access rights at the point of origin. These rights can be deep and involved. Here we keep it simple and open .
e) 
```

cp <somefile> /dev/storage/ 

```
where we test our setup to insure it is functional as we expect.
f)
```

ls -al /dev/storage

```
where we see that the test is good, we have a functional setup.
g)
```

sudo umount /mnt/storage

```
where we release the storage device. YOU mounted it .. YOU MUST unmount it .. failure to UNmount that device that YOU mounted will result in file system corruption in that data awaiting transfers ( including house keeping) does not get written if system is terminated with the device " in-use" . Always always UNmount what you mounted !


Next up is to decide if YOU want this storage device mounted at bootup .. or excluded such that it is mounted on demand. 
I must say I am prejudiced in favor of all the protection I can muster for my backup data, and I only mount my backup devices as "on demand" from terminal. Your use case (steam) may vary ! That is for you to decide.

Once you have done it a couple of times.
[INDENT][INDENT][INDENT]easy as falling out of bed wide awake
[/INDENT][/INDENT][/INDENT]

---

### Post by Boris786 on 2016-04-03
Good afternoon. Rightho I might have stumbled on step 1!

Creating mount point:
psas@psas-Bonobo-Extreme:/media/psas$ sudo mkdir -p /Mnt/HD2

Test to see if created:
psas@psas-Bonobo-Extreme:/media/psas$ ls
114ED27831533031  AC0AE6FD0AE6C404

Directory I think I have created does not appear?

---

### Post by oldfred on 2016-04-03
In Linux case is vital.
So /mnt is not /Mnt.
If you really want a new /Mnt as another folder off / (root), you have to create it.
But generally better to just use /mnt which already exists.

If you want name as hd2.
       sudo mkdir /mnt/hd2
sudo mount /dev/sdb1 /mnt/hd2
#where sdb1 needs to be your drive, partition
sudo chmod -R a+rwX,o-w /mnt/hd2
# Note that the -R is recursion and everything is changed, do NOT run on any system partitions.
#All directories will be 775.
#All files will be 664 except those that were set as executable to begin with.
sudo chown -R $USER:$USER /mnt/hd2

Unmount before using in fstab.

Then be sure to use correct UUID & /mnt/hd2 as mount in fstab entry.
      
 [http://ubuntuforums.org/showthread.php?t=1983336](http://ubuntuforums.org/showthread.php?t=1983336)
Mount & edit fstab from user Morbius1 in Post # 6 - suggest using templates instead.

---

### Post by Bashing-om on 2016-04-03
Boris786;Well ..

Not sure at all what we are looking at ..
Be aware linux is case sensitive such that /mnt DOES Not equal " /Mnt " .
We do want that mount point at a system directory '/mnt' for the purpose of this tutorial. So we remain on the same page.

From your home directory what returns from terminal command:
```

ls -al /media/psas/

```
I accept that in the /media directory the system keeps track of devices by the UUID ( that long string of alpha-numerics) .

And we continue this discussion from your point of reference; before returning to making the mount point in the /mnt directory.

[INDENT][INDENT]all a process of learning
[/INDENT][/INDENT]

---

### Post by Boris786 on 2016-04-04
ls -al /media/psas/ =

psas@psas-Bonobo-Extreme:~$ ls -al /media/psas
total 16
drwxr-x---+ 4 root root 4096 Apr  4 14:50 .
drwxr-xr-x  3 root root 4096 Mar 28 20:55 ..
drwx------  1 psas psas 4096 Apr  3 23:40 114ED27831533031
drwx------  1 psas psas 4096 Apr  4 08:04 AC0AE6FD0AE6C404

What I was expecting to see here was the mount point I thought I had created with sudo mkdir -p /Mnt/HD2 so in my mind I thought I would see directory mnt with sub directory HD2. 

This is slooow going. Bear with me and remain kind thanks.

---

### Post by Bashing-om on 2016-04-04
Boris786; Yeah ..

I too am a bit curios what is going on .. GVFS taking precedence ?
With the USB drives plugged in let's compare:
```

ls -al /media/psas/
sudo blkid
sudo parted -l

```
To cross reference the UUID with the device identifiers .

[INDENT][INDENT][INDENT]inquiring minds want to know
[/INDENT][/INDENT][/INDENT]

---

### Post by oldfred on 2016-04-04
If you do a mkdir /Mnt/HD2
That will be off / 
to see it then
cd /
ls -l

But still better to use /mnt since that already exists and avoids that confusion.

---

### Post by Boris786 on 2016-04-07
Ok I am not wedded to mounting in /media/<username>. It is jus that I felt there was an advantage to doing so: "GVFS file system  is aware and you then have access to the device from the GUI ( file  manager)".
If this is causing problems I am happy to simplify things and go to simplest which would be to use /mnt? My main aim (apart from learning)is to be able to put a steam game on my external hard drive.
Incidentally, do either of you have a recommendation on books/material for Ubuntu - I am currently looking at Ubuntu Unleashed, which I am not yet finding too heavy.
Back to business:
psas@psas-Bonobo-Extreme:~$ **ls -al /media/psas/**
total 8
drwxr-x---+ 2 root root 4096 Apr  4 17:38 .
drwxr-xr-x  3 root root 4096 Mar 28 20:55 ..

psas@psas-Bonobo-Extreme:~$** sudo blkid**

/dev/sda1: LABEL="System Reserved" UUID="8C20C33E20C32DD0" TYPE="ntfs" 
/dev/sda2: UUID="1AA6C50EA6C4EAF9" TYPE="ntfs" 
/dev/sdb1: UUID="114ED27831533031" TYPE="ntfs" 
/dev/sda3: UUID="25f3d659-a0df-4573-b6f1-b5c7979a3795" TYPE="ext4" 
/dev/sda5: UUID="22c12bf3-7d99-4988-882d-25dcf609bc9f" TYPE="ext4" 
/dev/sda6: UUID="6b354f2b-dc2e-44df-beb7-4e4f9fbbee7a" TYPE="ext4" 

psas@psas-Bonobo-Extreme:~$ **sudo parted -l**
Model: ATA INTEL SSDSC2CW12 (scsi)
Disk /dev/sda: 120GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type      File system  Flags
 1      1049kB  106MB   105MB   primary   ntfs         boot
 2      106MB   50.1GB  50.0GB  primary   ntfs
 3      50.1GB  50.6GB  500MB   primary   ext4
 4      50.6GB  120GB   69.4GB  extended
 5      50.6GB  80.6GB  30.0GB  logical   ext4
 6      80.6GB  120GB   39.4GB  logical   ext4


Model: ATA ST320LM001 HN-M3 (scsi)
Disk /dev/sdb: 320GB
Sector size (logical/physical): 512B/4096B
Partition Table: msdos

Number  Start   End    Size   Type     File system  Flags
 1      1049kB  320GB  320GB  primary  ntfs

Sorry I will be away for a week from today so will not be able to progeress anything on this until after the 17th April. Again thanks for the assistance.

---

### Post by Bashing-om on 2016-04-07
Boris786; Hey ..

Mounting in /media does have the advantage of direct access from the GUI tools , For instance a icon in the file manager pane.
However. my personal preference for security and adhering to a thought process is to mount from /mnt .

I look over what we have now .. and as you can see there is no provision at this time in " /media/psas/ " for the 2nd hard drive.
You can bet, as oldfred advised, that the mount point you created is :
```

ls -al /Mnt/

```
Keep in mind that the storage drive now seen as 'sdb' is formatted as the NTFS file system . One must make the access rights up from the mount in this use case .

Keeping also in mind oldfreds' advisements ->
We return to post #14. where we create the mount point in /mnt, and test by copying some arbitrary file to  the storage hard drive.

If the testing results are positive .. then we make the appropriate edits to the /etc/fstab config file for the permanent access means.
Either from /mnt or /media, where ever in the end you prefer.

We work here at your pace, your level of comprehension, and in your time frame. We do want you to know and understand.

[INDENT][INDENT]this ain't nothing but a thing
[/INDENT][/INDENT]

---

### Post by Boris786 on 2016-04-25
Hi,

Sorry been away so long. Extended break.
Back to business. A curious turn of events - went back to stage 14 and got:

psas@psas-Bonobo-Extreme:~$ sudo mount -t ntfs /dev/sdb1 /mnt/storage -o "umask=02
Mount is denied because the NTFS volume is already exclusively opened.
The volume may be already mounted, or another software may use it which
could be identified for example by the help of the 'fuser' command.
psas@psas-Bonobo-Extreme:~$ 

Then went onto Steam and appear to be able to download games. I do not really understand this but I can tell you I created a steam library under windows 10 pre this. So I am guessing this has done what I want.
What I really do not understand is that when I first attempted this I was in the same position as now. I had windows installed and a steam library in Windows but I could not add games to in Ubuntu.

Paul

---

### Post by Bashing-om on 2016-04-25
Boris786; Hey ..

A thought .. When normally shutting down Windows .. in actuality the system is hibernated and the hard drive is still in use ?
When quitting Windows now-a-days one must explicitly "quit" to free up the hardware .

[INDENT][INDENT]I thought I was wrong once before .. but ...
[/INDENT][/INDENT]

---

### Post by Boris786 on 2016-04-25
Thanks.
Yes actually this caused me to be unable to access the storage hard drive. I then set Windows to close down fully.
I am thinking it shuts down fully as I have no issues accessing.
I may be able to do what first set out to do but I cannot understand how I got here........
We might want to delete this thread when finished as I am not sure it is going to help anyone else! 
I guess I would still like to give my storage drive a label or name if it is not going to cause problems.When finished I am going to go away and learn more........

---

### Post by Boris786 on 2016-04-25
Nope not there. Steam games are not going to the extra 'storage' drive so I need to try to resolve the locked issue:
"psas@psas-Bonobo-Extreme:~$ sudo mount -t ntfs /dev/sdb1 /mnt/storage -o "umask=02
Mount is denied because the NTFS volume is already exclusively opened.
The volume may be already mounted, or another software may use it which
could be identified for example by the help of the 'fuser' command."
I will return to this tom, when a bit fresher. Any tips welcome.

---

### Post by oldfred on 2016-04-25
I believe Windows leaves all NTFS partitions mounted & then they all are hibernated. Even seem some users with external drives locked up. Turn off fast startup.

 Fast Startup off (always on hibernation)
[http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html](http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html)
[URL="http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.htmlold"]http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.htmlold

[/URL]
 Windows 7 unmount
[http://windows.microsoft.com/en-us/windows/mount-dismount-drive#1TC=windows-7](http://windows.microsoft.com/en-us/windows/mount-dismount-drive#1TC=windows-7) 

[URL="http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.htmlold"]
[/URL]

---

### Post by Boris786 on 2016-04-26
Thanks Oldfred,
I had turned off fast startup prior to this problem. Are you saying I need to unmount the drive in windows and then try in Linux on top of this?
My intention is to move to Linux long term once I have worked it out but it seems my dual boot approach is causing problems in itself.
I might give up on this and when I am happy take off Windows and go with Ubuntu.

---

### Post by oldfred on 2016-04-26
If fast start up off, then the Linux NTFS driver should be able to mount the NTFS partition(s).
And Windows on updates will turn fast start up back on.
The other issue can be if a NTFS partition needs chkdsk then it will not mount it to prevent damage that chkdsk might not be able to repair.

There is a way to force mount in read only mode if required.

---

### Post by Boris786 on 2016-04-29
OK I am now full fat Ubuntu 14.04, with no Windows. I have created mount point and can access and copy files onto my additional hard drive:
boris@boris-Bonobo-Extreme:/media$ ls
boris  mount
boris@boris-Bonobo-Extreme:/media$ ls mount
HOME.zip  lost+found
boris@boris-Bonobo-Extreme:/media$ 

I used guidance here: [http://docs.system76.com/articles/extraDrive/](http://docs.system76.com/articles/extraDrive/)

This worked and I can now download steam games :-). Thanks for all the help given. 

No real idea why it worked this time.

---

