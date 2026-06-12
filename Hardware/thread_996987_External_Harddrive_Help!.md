---
title: "External Harddrive Help!"
date: 2008-11-29
forum: Hardware
---

### Post by BlackRoseBud on 2008-11-29
Using Ubuntu Intrepid.  I got an external hard drive to back all my files up from a windows computer.  Formatted it NTFS thinking this was best to use for Windows, but now I wish I used FAT.  Well when I put all the files on the hard drive, I disconnected the drive by pulling out the USB cord, the same way you would any flash drive and now I can't access anything on the hard drive!  I've already formatted that windows computer, so I can't go back and safely-remove.  When I plug it into a windows machine, nothing happens, but in Ubuntu I get this message: 

$LogFile indicates unclean shutdown (0,1) Failed to mount '/dev/sdb1': Operation not supported Mount is denied because NTFS is marked to be in use. Choose one action: Choice 1: If you have Windows then disconnect the external devices by clicking on the 'Safely Remove Hardware' icon in the Windows taskbar then shutdown Windows cleanly.  Choice 2: If you don't have Windows then you can use the 'force' option for your own responsibility.  For example type on the command line: mount -t ntfs-3g /dev/sdb1 /media/Volume Name -o force  Or add the option ot the relevant row in the /etc/fstab file: /dev/sdb1 /media/Volume Name ntfs-3g force 0 0

So I tried typing the "mount -t ntfs-3g /dev/sdb1 /media/Volume Name -o force" command in a terminal replacing Volume Name with my drive's Volume name and it doesn't work.  The thing just comes up with these instructions on how to use mount:

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

I appreciate any help anyone can give me. I'm freakin out right now.

---

### Post by taurus on 2008-11-29
Pulling it out without using the Safely Remove Hardware in windows is never a good thing. 

What happens when you run these from a terminal?

```
sudo mkdir /media/sdb1
sudo mount -t ntfs-3g /dev/sdb1 /media/sdb1 -o force
```

---

### Post by cdtech on 2008-11-29
> **BlackRoseBud said:**
> $LogFile indicates unclean shutdown (0,1) Failed to mount '/dev/sdb1': Operation not supported Mount is denied because NTFS is marked to be in use.

Use this command to reset the NTFS journal:
```
ntfsfix
```
You may need to install the tools:
```
sudo apt-get install ntfstools
```

---

### Post by BlackRoseBud on 2008-11-29
> **taurus said:**
> Pulling it out without using the Safely Remove Hardware in windows is never a good thing. 

What happens when you run these from a terminal?

```
sudo mkdir /media/sdb1
sudo mount -t ntfs-3g /dev/sdb1 /media/sdb1 -o force
```

That fixes everything is what happens.  Thank!  The drive now mounts and unmounts normally both in Linux and Windows.

Why did the makers of the NTFS file system create such a crappy failsafe?  I'd rather have a corrupt file than an inoperable drive any day.

It would be nice to see an option to force mount from within the Gnome Interface.

---

### Post by trooperchix on 2008-11-30
This is all just not working for me.  I have an old internal harddrive mounted in an external enclosure that connects to my laptop via usb.  I want to set up this external drive as an additional available drive (for backups and additional space for my music files.  Here's what I tried below:

```
 
eddie@kilimanjaro:~$ sudo mkdir /media/sdb1
[sudo] password for eddie: 
eddie@kilimanjaro:~$ sudo mount -t ntfs-3g /dev/sdb1 /media/sdb1 -o force
NTFS signature is missing.
Failed to mount '/dev/sdb1': Invalid argument
The device '/dev/sdb1' doesn't have a valid NTFS.
Maybe you selected the wrong device? Or the whole disk instead of a
partition (e.g. /dev/hda, not /dev/hda1)? Or the other way around?
eddie@kilimanjaro:~$ ntfsfix
The program 'ntfsfix' is currently not installed.  You can install it by typing:
sudo apt-get install ntfsprogs
bash: ntfsfix: command not found
eddie@kilimanjaro:~$ sudo apt-get install ntfsprogs
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  lincity-ng-data python-libuser linux-headers-2.6.27-7 libsdl-gfx1.2-4
  linux-headers-2.6.27-7-generic libsdl-ttf2.0-0 libphysfs-1.0-0 libuser1
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  libntfs10
The following NEW packages will be installed:
  libntfs10 ntfsprogs
0 upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
Need to get 391kB of archives.
After this operation, 950kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 http://se.archive.ubuntu.com intrepid/main libntfs10 2.0.0-1ubuntu2 [122kB]
Get:2 http://se.archive.ubuntu.com intrepid/main ntfsprogs 2.0.0-1ubuntu2 [269kB]
Fetched 391kB in 2s (152kB/s)     
Selecting previously deselected package libntfs10.
(Reading database ... 163683 files and directories currently installed.)
Unpacking libntfs10 (from .../libntfs10_2.0.0-1ubuntu2_i386.deb) ...
Selecting previously deselected package ntfsprogs.
Unpacking ntfsprogs (from .../ntfsprogs_2.0.0-1ubuntu2_i386.deb) ...
Processing triggers for man-db ...
Setting up libntfs10 (2.0.0-1ubuntu2) ...

Setting up ntfsprogs (2.0.0-1ubuntu2) ...
Processing triggers for libc6 ...
ldconfig deferred processing now taking place
eddie@kilimanjaro:~$ ntfsfix
ERROR: You must specify a device.
ntfsfix v2.0.0 (libntfs 10:0:0)

Usage: ntfsfix [options] device
    Attempt to fix an NTFS partition.

    -h, --help             Display this help
    -V, --version          Display version information

For example: ntfsfix /dev/hda6

Developers' email address: linux-ntfs-dev@lists.sf.net
Linux NTFS homepage: http://www.linux-ntfs.org
eddie@kilimanjaro:~$ ntfsfix /media/sdb1
Mounting volume... Error opening partition device: Is a directory.
Failed to startup volume: Is a directory.
FAILED
Attempting to correct errors... Error opening partition device: Is a directory.
FAILED
Failed to startup volume: Is a directory.
Volume is corrupt. You should run chkdsk.
eddie@kilimanjaro:~$ chkdsk /media/sdb1
bash: chkdsk: command not found
eddie@kilimanjaro:~$ sudo mount -t ntfs-3g /dev/sdb1 /media/sdb1 -o force
NTFS signature is missing.
Failed to mount '/dev/sdb1': Invalid argument
The device '/dev/sdb1' doesn't have a valid NTFS.
Maybe you selected the wrong device? Or the whole disk instead of a
partition (e.g. /dev/hda, not /dev/hda1)? Or the other way around?
eddie@kilimanjaro:~$ 

```

Help!!!

---

### Post by taurus on 2008-11-30
> **trooperchix said:**
> This is all just not working for me.  I have an old internal harddrive mounted in an external enclosure that connects to my laptop via usb.  I want to set up this external drive as an additional available drive (for backups and additional space for my music files.  Here's what I tried below:

```
 
eddie@kilimanjaro:~$ sudo mkdir /media/sdb1
[sudo] password for eddie: 
eddie@kilimanjaro:~$ sudo mount -t ntfs-3g /dev/sdb1 /media/sdb1 -o force
NTFS signature is missing.
Failed to mount '/dev/sdb1': Invalid argument
The device '/dev/sdb1' doesn't have a valid NTFS.
Maybe you selected the wrong device? Or the whole disk instead of a
partition (e.g. /dev/hda, not /dev/hda1)? Or the other way around?
eddie@kilimanjaro:~$ ntfsfix
The program 'ntfsfix' is currently not installed.  You can install it by typing:
sudo apt-get install ntfsprogs
bash: ntfsfix: command not found
eddie@kilimanjaro:~$ sudo apt-get install ntfsprogs
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  lincity-ng-data python-libuser linux-headers-2.6.27-7 libsdl-gfx1.2-4
  linux-headers-2.6.27-7-generic libsdl-ttf2.0-0 libphysfs-1.0-0 libuser1
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  libntfs10
The following NEW packages will be installed:
  libntfs10 ntfsprogs
0 upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
Need to get 391kB of archives.
After this operation, 950kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 http://se.archive.ubuntu.com intrepid/main libntfs10 2.0.0-1ubuntu2 [122kB]
Get:2 http://se.archive.ubuntu.com intrepid/main ntfsprogs 2.0.0-1ubuntu2 [269kB]
Fetched 391kB in 2s (152kB/s)     
Selecting previously deselected package libntfs10.
(Reading database ... 163683 files and directories currently installed.)
Unpacking libntfs10 (from .../libntfs10_2.0.0-1ubuntu2_i386.deb) ...
Selecting previously deselected package ntfsprogs.
Unpacking ntfsprogs (from .../ntfsprogs_2.0.0-1ubuntu2_i386.deb) ...
Processing triggers for man-db ...
Setting up libntfs10 (2.0.0-1ubuntu2) ...

Setting up ntfsprogs (2.0.0-1ubuntu2) ...
Processing triggers for libc6 ...
ldconfig deferred processing now taking place
eddie@kilimanjaro:~$ ntfsfix
ERROR: You must specify a device.
ntfsfix v2.0.0 (libntfs 10:0:0)

Usage: ntfsfix [options] device
    Attempt to fix an NTFS partition.

    -h, --help             Display this help
    -V, --version          Display version information

For example: ntfsfix /dev/hda6

Developers' email address: linux-ntfs-dev@lists.sf.net
Linux NTFS homepage: http://www.linux-ntfs.org
eddie@kilimanjaro:~$ ntfsfix /media/sdb1
Mounting volume... Error opening partition device: Is a directory.
Failed to startup volume: Is a directory.
FAILED
Attempting to correct errors... Error opening partition device: Is a directory.
FAILED
Failed to startup volume: Is a directory.
Volume is corrupt. You should run chkdsk.
eddie@kilimanjaro:~$ chkdsk /media/sdb1
bash: chkdsk: command not found
eddie@kilimanjaro:~$ sudo mount -t ntfs-3g /dev/sdb1 /media/sdb1 -o force
NTFS signature is missing.
Failed to mount '/dev/sdb1': Invalid argument
The device '/dev/sdb1' doesn't have a valid NTFS.
Maybe you selected the wrong device? Or the whole disk instead of a
partition (e.g. /dev/hda, not /dev/hda1)? Or the other way around?
eddie@kilimanjaro:~$ 

```

Help!!!

Can you post the output of this command from a terminal?

```
sudo fdisk -l
```

---

### Post by trooperchix on 2008-11-30
> **taurus said:**
> Can you post the output of this command from a terminal?

```
sudo fdisk -l
```

I happen to be having from what I can tell the exact same problem.  Here's my output of above:

```


eddie@kilimanjaro:~$ sudo fdisk -l

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000e2777

   Device Boot      Start         End      Blocks   Id  System
/dev/sda2             370       19457   153324360    5  Extended
/dev/sda5           18705       19457     6048441   82  Linux swap / Solaris
/dev/sda6   *         370       17954   141251449+  83  Linux
/dev/sda7           17955       18704     6024343+  82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xb623b623

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        9729    78148161    5  Extended
eddie@kilimanjaro:~$ 

```

What next?  What do I have to do to mount the sdb1 hard drive?

---

### Post by taurus on 2008-11-30
> **trooperchix said:**
> I happen to be having from what I can tell the exact same problem.  Here's my output of above:

```


eddie@kilimanjaro:~$ sudo fdisk -l

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000e2777

   Device Boot      Start         End      Blocks   Id  System
/dev/sda2             370       19457   153324360    5  Extended
/dev/sda5           18705       19457     6048441   82  Linux swap / Solaris
/dev/sda6   *         370       17954   141251449+  83  Linux
/dev/sda7           17955       18704     6024343+  82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xb623b623

   Device Boot      Start         End      Blocks   Id  System
**[COLOR="Blue"]/dev/sdb1               1        9729    78148161    5  Extended[/COLOR]**
eddie@kilimanjaro:~$ 

```

What next?  What do I have to do to mount the sdb1 hard drive?

It, /dev/sdb1, is an extended partition so you actually need to create a logical partition, /dev/sdb5, and format it with a filesystem before you can use it.  So, use gparted from System -> Administration (install it if you don't have it) and either delete that partition and create a new primary partition on your second harddrive and format it to whatever filesystem you want to use, or create a new logical partition, /dev/sdb5, and format it.

---

### Post by trooperchix on 2008-11-30
Ok, let me do that again.  I did change it to sdb5 logical drive.  It is now recognized as a usb drive.  *BUT* I get some stupid error that states:

Error while copying
The folder "PDF" cannot be copied because you do not have permissions to create it in the destination.  

here's my ```
 sudo fdsk -l 
``` again:
```

eddie@kilimanjaro:~$ sudo fdisk -l
[sudo] password for eddie: 

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000e2777

   Device Boot      Start         End      Blocks   Id  System
/dev/sda2             370       19457   153324360    5  Extended
/dev/sda5           18705       19457     6048441   82  Linux swap / Solaris
/dev/sda6   *         370       17954   141251449+  83  Linux
/dev/sda7           17955       18704     6024343+  82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xb623b623

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        9729    78148161    5  Extended
/dev/sdb5               1        9729    78148129+  83  Linux
eddie@kilimanjaro:~$ 

```

---

### Post by taurus on 2008-11-30
You just need to change the mount point for /dev/sdb5 from root to your login name so you can write to it because root is the owner of that mount point right now.  Looks like your username is eddie; I assume you have mounted your /dev/sdb5 to /media/sdb1.

```
sudo chown -R eddie:eddie /media/sdb1
ls -la /media
```
Now, see if you can copy anything to /media/sdb1 as eddie.

---

### Post by trooperchix on 2008-11-30
> **taurus said:**
> Can you post the output of this command from a terminal?

```
sudo fdisk -l
```

> **taurus said:**
> You just need to change the mount point for /dev/sdb5 from root to your login name so you can write to it because root is the owner of that mount point right now.  Looks like your username is eddie; I assume you have mounted your /dev/sdb5 to /media/sdb1.

```
sudo chown -R eddie:eddie /media/sdb1
ls -la /media
```
Now, see if you can copy anything to /media/sdb1 as eddie.


Ok, followed your instructions, and still I cannot copy anything to my internal hd to that external sdb5 drive.  Again, fits over permissions..

Any other ideas?

---

### Post by trooperchix on 2008-12-01
* bump *

---

### Post by trooperchix on 2008-12-01
*bump*

---

### Post by taurus on 2008-12-01
Did you change the ownership of /media/sdb1 from root to your login name, eddie?

What are the outputs of these commands from a terminal?

```
df -h
ls -la /media
```

---

### Post by trooperchix on 2008-12-01
> **taurus said:**
> Did you change the ownership of /media/sdb1 from root to your login name, eddie?

What are the outputs of these commands from a terminal?

```
df -h
ls -la /media
```

I don't know how to change the ownership of /media/sdb1 from root to my login

```

eddie@kilimanjaro:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda6             134G  107G   21G  85% /
tmpfs                1008M     0 1008M   0% /lib/init/rw
varrun               1008M  108K 1008M   1% /var/run
varlock              1008M     0 1008M   0% /var/lock
udev                 1008M  2.8M 1005M   1% /dev
tmpfs                1008M  104K 1008M   1% /dev/shm
lrm                  1008M  2.0M 1006M   1% /lib/modules/2.6.27-9-generic/volatile
/dev/sdb5              74G   52M   70G   1% /media/disk
eddie@kilimanjaro:~$ ls -la /media
total 24
drwxr-xr-x  5 root  root  4096 2008-12-01 14:49 .
drwxr-xr-x 21 root  root  4096 2008-11-27 20:36 ..
lrwxrwxrwx  1 root  root     6 2008-05-05 21:09 cdrom -> cdrom0
drwxr-xr-x  2 root  root  4096 2008-05-05 21:09 cdrom0
drwxr-xr-x  3 root  root  4096 2008-11-30 17:21 disk
-rw-r--r--  1 root  root    59 2008-12-01 14:49 .hal-mtab
-rw-------  1 root  root     0 2008-12-01 14:49 .hal-mtab-lock
drwxr-xr-x  2 eddie eddie 4096 2008-11-30 11:41 sdb1
eddie@kilimanjaro:~$ 

```

---

### Post by taurus on 2008-12-01
> **trooperchix said:**
> I don't know how to change the ownership of /media/sdb1 from root to my login

```

eddie@kilimanjaro:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda6             134G  107G   21G  85% /
tmpfs                1008M     0 1008M   0% /lib/init/rw
varrun               1008M  108K 1008M   1% /var/run
varlock              1008M     0 1008M   0% /var/lock
udev                 1008M  2.8M 1005M   1% /dev
tmpfs                1008M  104K 1008M   1% /dev/shm
lrm                  1008M  2.0M 1006M   1% /lib/modules/2.6.27-9-generic/volatile
**/dev/sdb5              74G   52M   70G   1% /media/disk**
eddie@kilimanjaro:~$ ls -la /media
total 24
drwxr-xr-x  5 root  root  4096 2008-12-01 14:49 .
drwxr-xr-x 21 root  root  4096 2008-11-27 20:36 ..
lrwxrwxrwx  1 root  root     6 2008-05-05 21:09 cdrom -> cdrom0
drwxr-xr-x  2 root  root  4096 2008-05-05 21:09 cdrom0
**drwxr-xr-x  3 root  root  4096 2008-11-30 17:21 disk**
-rw-r--r--  1 root  root    59 2008-12-01 14:49 .hal-mtab
-rw-------  1 root  root     0 2008-12-01 14:49 .hal-mtab-lock
drwxr-xr-x  2 eddie eddie 4096 2008-11-30 11:41 sdb1
eddie@kilimanjaro:~$ 

```

Okay, you mount your external harddrive, /dev/sdb5 (logical partition), to /media/disk, not /media/sdb1.  So technically, root is still the owner of that mount point.  Do

```
sudo chown -R eddie:eddie /media/disk
ls -la /media
```
Is that external drive plugged in all the time?

---

### Post by trooperchix on 2008-12-01
> 
Okay, you mount your external harddrive, /dev/sdb5 (logical partition), to /media/disk, not /media/sdb1. So technically, root is still the owner of that mount point. Do

Code:

sudo chown -R eddie:eddie /media/disk
ls -la /media

Is that external drive plugged in all the time?


Alright, it's working now.  No, it isn't hooked up all the time, is that an issue?

---

### Post by taurus on 2008-12-01
When you unmount your external harddrive, the automount program will remove /media/disk so the next time you plug it in, root will probably be the owner of /media/disk again so if you want to write to it, you have to use chown to change the ownership of /media/disk.

---

### Post by trooperchix on 2008-12-02
Your solution worked perfectly.  I did a fresh reinstall of Ibex, and I know I can take information from that sdb1 drive, I haven't tried to put stuff on it, but I would imagine if I can take, I can place files.

---

