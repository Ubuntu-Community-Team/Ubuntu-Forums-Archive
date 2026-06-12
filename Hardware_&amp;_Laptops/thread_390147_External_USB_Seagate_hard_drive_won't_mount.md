---
title: "External USB Seagate hard drive won't mount"
date: 2007-03-21
forum: Hardware &amp; Laptops
---

### Post by jarocooke on 2007-03-21
Hi,

I am just trying out Feisty and for some reason it won't seem to mount my external USB Seagate hard drive.

```

Mar 21 20:05:50 jaro-laptop kernel: [ 1338.224000] usb 5-3: new high speed USB device using ehci_hcd and address 9
Mar 21 20:05:50 jaro-laptop kernel: [ 1338.360000] usb 5-3: configuration #1 chosen from 1 choice
Mar 21 20:05:50 jaro-laptop kernel: [ 1338.360000] scsi5 : SCSI emulation for USB Mass Storage devices
Mar 21 20:05:55 jaro-laptop kernel: [ 1343.360000] scsi 5:0:0:0: Direct-Access     Seagate  External Drive        PQ: 0 ANSI: 0
Mar 21 20:05:55 jaro-laptop kernel: [ 1343.364000] SCSI device sdb: 625142448 512-byte hdwr sectors (320073 MB)
Mar 21 20:05:55 jaro-laptop kernel: [ 1343.364000] sdb: Write Protect is off
Mar 21 20:05:55 jaro-laptop kernel: [ 1343.364000] SCSI device sdb: 625142448 512-byte hdwr sectors (320073 MB)
Mar 21 20:05:55 jaro-laptop kernel: [ 1343.364000] sdb: Write Protect is off
Mar 21 20:05:55 jaro-laptop kernel: [ 1343.364000]  sdb: sdb1
Mar 21 20:05:55 jaro-laptop kernel: [ 1343.380000] sd 5:0:0:0: Attached scsi disk sdb
Mar 21 20:05:55 jaro-laptop kernel: [ 1343.380000] sd 5:0:0:0: Attached scsi generic sg2 type 0

```

These are the relevant log entries created when I turn on the drive.  I have tried mounting the drive using the mount command and it simply stated that I must specify the filesystem (usually meaning I am trying to mount a non-existent partition).

Does anyone know how I can get access to the drive though Feisty?

What exactly is the problem here (for interest)?  Edgy had no problem at all, I did wonder whether it was related to [Bug #61235]("https://launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/61235") (USB mass storage stops working after a while), but having looked at the logs I don't think it is.

Any help and information on this problem would be greatly appreciated, as I can't think what else to do.  All searches in the forums have turned up nothing so far.

Cheers

---

### Post by taurus on 2007-03-21
Post the output of this command from a terminal here.

```
sudo fdisk -l
```
Is there a filesystem/partition on that USB drive?

---

### Post by jarocooke on 2007-03-21
I ran the command, the output is below.

```

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9352    75119908+  83  Linux
/dev/sda2            9353        9729     3028252+   5  Extended
/dev/sda5            9353        9729     3028221   82  Linux swap / Solaris

Disk /dev/sdb: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       38913   312568641    c  W95 FAT32 (LBA)

Disk /dev/sdc: 2079 MB, 2079850496 bytes
17 heads, 32 sectors/track, 7467 cylinders
Units = cylinders of 544 * 512 = 278528 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1        7468     2031087+   6  FAT16

```

I don't know where sdc1 came from, it was sdb1 earlier.

The drive is formatted using vfat according to system monitor (seen in Edgy, not present in Feisty).

The drive definitely has lots of information on it (all my backups).

Cheers

---

### Post by taurus on 2007-03-21
There is already /dev/sdb1 so the second USB device is known as /dev/sdc1 (since you have a SATA drive--/dev/sda).  To mount it, open a terminal and run

```
sudo mkdir /media/windows
sudo mount -t vfat /dev/sdc1 /media/windows -o iocharset=utf8,umask=000
df -h
```

---

### Post by jarocooke on 2007-03-21
Wow, your a star!
:guitar: 
I have access to the data.  Do you know why Ubuntu didn't automatically mount it and show an icon on the desktop?

---

### Post by lilnerd on 2007-04-12
> **jarocooke said:**
> Wow, your a star!
:guitar: 
I have access to the data.  Do you know why Ubuntu didn't automatically mount it and show an icon on the desktop?

Can you help me to. I get this.
> Disk /dev/hda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        7649    61440561    7  HPFS/NTFS
/dev/hda2            7650        7713      514080   82  Linux swap / Solaris
/dev/hda3            7714        9729    16193520   83  Linux

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       30401   244196001    7  HPFS/NTFS
anand@anand-room:~$ 


---

### Post by lilnerd on 2007-04-12
> **lilnerd said:**
> Can you help me to. I get this.
Sry this might be more easy to read.

```
Disk /dev/hda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        7649    61440561    7  HPFS/NTFS
/dev/hda2            7650        7713      514080   82  Linux swap / Solaris
/dev/hda3            7714        9729    16193520   83  Linux

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       30401   244196001    7  HPFS/NTFS
anand@anand-room:~$ 

```

---

### Post by taurus on 2007-04-12
> **lilnerd said:**
> Sry this might be more easy to read.

```
Disk /dev/hda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        7649    61440561    7  HPFS/NTFS
/dev/hda2            7650        7713      514080   82  Linux swap / Solaris
/dev/hda3            7714        9729    16193520   83  Linux

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       30401   244196001    7  HPFS/NTFS
anand@anand-room:~$ 

```

Edit /etc/fstab

```
gksudo gedit /etc/fstab
```
and add these two lines to the end of it.

```
/dev/hda1   /media/hda1   ntfs   nls=utf8,umask=0222   0  0
/dev/sda1   /media/sda1   ntfs   nls=utf8,umask=0222   0  0
```
Save the changes.  Then, create two new mount points and mount them.

```
sudo mkdir /media/hda1 /media/sda1
sudo mount -a
df -h
```

---

### Post by lilnerd on 2007-04-12
> **taurus said:**
> Edit /etc/fstab

```
gksudo gedit /etc/fstab
```
and add these two lines to the end of it.

```
/dev/hda1   /media/hda1   ntfs   nls=utf8,umask=0222   0  0
/dev/sda1   /media/sda1   ntfs   nls=utf8,umask=0222   0  0
```
Save the changes.  Then, create two new mount points and mount them.

```
sudo mkdir /media/hda1 /media/sda1
sudo mount -a
df -h
```

Wow Quick Reply. Thanks, but know I am having read/write issues with permissions. I got ntfs-3g config but its not working:( So now i can put songs on my hard drive but not read or copy them from windows. Can you help me with this.
Thanks
Lilnerd

---

### Post by taurus on 2007-04-12
You want to write to your ntfs filesystem.  How did you mount your ntfs partitons then?  Post your /etc/fstab here.

```
cat /etc/fstab
```

[http://ubuntuforums.org/showthread.php?t=217009](http://ubuntuforums.org/showthread.php?t=217009)

---

### Post by EnigMattic on 2007-04-17
Disk /dev/sda: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        6992    56163208+  83  Linux
/dev/sda2            6993        7296     2441880    5  Extended
/dev/sda5            6993        7296     2441848+  82  Linux swap / Solaris

Disk /dev/sdb: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       38913   312568641    c  W95 FAT32 (LBA)

**PLEASE HELP!!!!!** /dev/sdb1 should be mounting automatically! What's up with Feisty??? :-(

---

### Post by sque on 2007-04-19
I am in same case with an external hard-drive not mounting automatically by gnome. From a fast search I see that pmount is missing and now the feisty doesn't (?) depends on this but on gnome-mount (Am I right?). Why isn't this working. What should we do?

---

### Post by FrancoNero on 2007-04-19
i have a seagate at home, i'll try tomorrow and post my experiences... but from what i've read here, i am disappointed with feisty. people talking about 3d effects and stuff, while the basic stuff doesn't even work :-(

---

### Post by sque on 2007-04-20
Ahmm wierd things happen... 

After mounting it by hand on the /media (mount command) the gnome showed the 2 partitions of the external disc in "my computer" and on dekstop BUT right click properties didn't show the usual tabs of hard drivers ("Drive" and "Volume") they were more like simple shortcuts. After that I tried to reboot the pc and voila! the gnome did the auto mount correctly:)

But I dont know what could fixed it.
* Maybe the manual mount at /media wakes up gnome about the external hard drive.. ^o)
* I just installed and uninstall pmount without using it. maybe it added an additional dependency of it.

PS. One of the things I dont like with ubuntu is that as the versions come and go, the bugs are grown and speed is decreasing... Many times I start missing gentoo (although compiling X may took 3 years :P ). 
PS2: My external hard drive is not seagete its an internal WD 250gb modified with ata->usb case. And there is no problem with the drivers, kernel reports it correctly and mount by hand worked just fine.

---

### Post by tobydecks on 2007-05-10
Same here too :(

I have a 400Gb Seagate External USB Drive
With Edgy, it was no problem at all, and mounted on boot.

Have tried combinations of unplugging/plugging, on/off etc, but no joy.

Got this output, but am a real n00b, so doesn't make a whole lot of sense....

```
Disk /dev/hda: 8455 MB, 8455200768 bytes
255 heads, 63 sectors/track, 1027 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1         981     7879851   83  Linux
/dev/hda2             982        1027      369495    5  Extended
/dev/hda5             982        1027      369463+  82  Linux swap / Solaris

Disk /dev/hdb: 30.0 GB, 30020272128 bytes
255 heads, 63 sectors/track, 3649 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1        1825    14659281    7  HPFS/NTFS
/dev/hdb2            1826        3649    14651280    f  W95 Ext'd (LBA)
/dev/hdb5            1826        3649    14651248+   7  HPFS/NTFS

Disk /dev/sda: 400.0 GB, 400088457216 bytes
255 heads, 63 sectors/track, 48641 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       48641   390708801    c  W95 FAT32 (LBA)
```

I assume its /dev/sda1 that's the offender?
Do I need to edit fstab?
If so, what do I need to change?

Any help would be great

Cheers
:)

---

### Post by X3N on 2007-05-14
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+bug/102097](https://bugs.launchpad.net/ubuntu/+bug/102097) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				try: pmount -t /dev/sda1

---

### Post by tbg58 on 2007-05-28
I experienced the same problem.  After I reformatted the drive as ext3, it automounts with no problems.
[http://ubuntuforums.org/showthread.php?t=456689&highlight=seagate+250gb+usb](http://ubuntuforums.org/showthread.php?t=456689&highlight=seagate+250gb+usb)

Hope this helps!
Good luck!
Rob

---

### Post by Go99an on 2007-06-08
Hi Folks,
This thread seems the closest fit to the problem that I am having....

I have a USB ntfs disk that I am unable to see/access. I have tried fdisk -l and it is showing up as being /dev/sda1 and a 123gb disk. I have also downloaded the ntfs-3g utility from Automatix2.

Could anyone help me with setting this up so that I can use it and also so that I can upload all of the data that I want to keep on my Kubuntu Laptop.


Here are some of the outputs to a number of the suggested commands;


duncan@Go99U:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=ebd9cb41-1a8e-42ff-a674-cc9e2bf64cbd /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=a4068b01-ee62-47de-806a-11dc711432fe none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0

# Generated by Automatix
## End of Automatix mounted partitions


duncan@Go99U:~$ fdisk -l

Disk /dev/sda: 123.5 GB, 123522416640 bytes
255 heads, 63 sectors/track, 15017 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       15017   120624021    7  HPFS/NTFS


duncan@Go99U:~$ uname -r
2.6.20-16-generic


I would be most grateful if someone could help me set this disk up as I feel sure that it is only a few well chosen commands that one of you 'Guru's' know......

Regards,
Go99an.

---

