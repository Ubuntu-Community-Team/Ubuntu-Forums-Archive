---
title: "Having problems mounting my new Seagate Backup Plus 4TB external drive"
date: 2016-08-17
forum: Hardware
---

### Post by pappo2 on 2016-08-17
I am using Ubuntu 16.04.  I purchased a Seagate Backup Plus 4TB external drive.
When I rebooted I can see that the system created two directories.

 /media/phillip/Seagate Backup Plus

drwx------ 2 root root 4096 Jun  1 11:22 Seagate Backup Plus Drive
drwx------ 2 root root 4096 Aug 17 13:45 Seagate Backup Plus Drive1

When I try to mount the drive I get the following:

phillip@homeserver:/media/phillip$ sudo mount -t ntfs /dev/sdc1 /media/phillip/Seagate\ Backup\ Plus\ Drive1
Error reading bootsector: Input/output error
Failed to mount '/dev/sdc1': Input/output error
NTFS is either inconsistent, or there is a hardware fault, or it's a
SoftRAID/FakeRAID hardware. In the first case run chkdsk /f on Windows
then reboot into Windows twice. The usage of the /f parameter is very
important! If the device is a SoftRAID/FakeRAID then first activate
it and mount a different device under the /dev/mapper/ directory, (e.g.
/dev/mapper/nvidia_eahaabcc1). Please see the 'dmraid' documentation
for more details.

How, or what programs, can I use to test this Seagate drive and see if needs repair?

Any help would be appreciated.

---

### Post by yancek on 2016-08-17
The "inconsistent" message is often a result of having the disk used on a windows system such as 8 or 10 which always uses hibernation/fast start.  Did you have this drive attached to a windows system?  Linux will not mount an ntfs partition in an inconsistent state.

You indicate that you "rebooted" but not what you were booted to.  Did you use this drive, put any data on it?

---

### Post by weatherman2 on 2016-08-17
Please open a terminal in Ubuntu (Ctrl alt t) with this drive plugged in, then please type these commands then show the results here:

```

sudo parted -l
df

```

Typically, with an off-the-shelf portable drive, I just click on the drive partition in "File Manager" (or the "Places" menu depending on your version of Ubuntu) to mount it instead of typing a command.  Sometimes the drive partition gets mounted automatically when you plug it in.

FYI, I don't use the /media directory to mount partitions manually - I leave /media to the Nautilus software to use for mounting stuff and use the /mnt directory for mounting stuff manually.  If your partition really is /dev/sdc1 then I would mount it this way:

```

sudo mkdir -p /mnt/MyDrive
sudo mount /dev/sdc1 /mnt/MyDrive

```

Then navigate to /mnt/MyDrive to see the stuff on my drive.  But with a typical USB drive, as I said above, I would click on the drive partition in the "File Manager" icon to mount it.

---

### Post by pappo2 on 2016-08-18
Thank you for the replies.
The Seagate drive in question is   /dev/sdc

The drive was being used on a Windows 10 system before I moved it to my Ubuntu 16.04 system.  I had trouble using it on Win10 so I moved it to the PC (Ubuntu) that I use for my home fileserver.
When I first connected the drive, the system automatically mounted it at the following location:

/media/phillip/Seagate Backup Plus Drive1

total 4
drwx------ 2 root root 4096 Jun  1 11:22 Seagate Backup Plus Drive

================================================

Here is the output from parted -l

sudo parted -l
Model: ATA WDC WD5000AADS-0 (scsi)
Disk /dev/sda: 500GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos
Disk Flags:
Number  Start   End     Size    Type      File system     Flags
 1      1049kB  21.0GB  21.0GB  primary   ext4            boot
 3      21.0GB  498GB   477GB   primary   ext4
 2      498GB   500GB   2144MB  extended
 5      498GB   500GB   2144MB  logical   linux-swap(v1)

Model: ATA WDC WD5000AACS-0 (scsi)
Disk /dev/sdb: 500GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos
Disk Flags:
Number  Start   End    Size   Type     File system  Flags
 1      1049kB  500GB  500GB  primary  ext4         lvm

Error: /dev/sdc: unrecognised disk label
Model:  (file)
Disk /dev/sdc: 65.5kB
Sector size (logical/physical): 512B/512B
Partition Table: unknown
Disk Flags:


===================================

Here is the result from df:

$ df
Filesystem     1K-blocks      Used Available Use% Mounted on
udev             1846964        28   1846936   1% /dev
tmpfs             372952     25112    347840   7% /run
/dev/sda1       20017020   6403452  12573696  34% /
tmpfs            1864744       152   1864592   1% /dev/shm
tmpfs               5120         4      5116   1% /run/lock
tmpfs            1864744         0   1864744   0% /sys/fs/cgroup
/dev/sda3      458379464 262801692 172270408  61% /home
cgmfs                100         0       100   0% /run/cgmanager/fs
tmpfs             372952        16    372936   1% /run/user/1000
/dev/sdb1      480589520 290620320 165533540  64% /home/phillip/allusers

---

### Post by pappo2 on 2016-08-18
One more thing.  
I tried to clear the drive, because I have another one with my data, so I could reformat it as a ext4 instead of ntfs.
I apparently messed that up and now the drive has no partition and cannot be mounted.

Here is the output from fdisk /dev/sdc

~$ sudo fdisk  /dev/sdc


Welcome to fdisk (util-linux 2.27.1).
Changes will remain in memory only, until you decide to write them.
Be careful before using the write command.
Device does not contain a recognized partition table.
Created a new DOS disklabel with disk identifier 0xb7095af4.


Command (m for help): p
Disk /dev/sdc: 64 KiB, 65536 bytes, 128 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0xb7095af4



It does not appear to show the disk as being 4TB.
When I try to add a new partition I get this:

Command (m for help): n
Partition type
   p   primary (0 primary, 0 extended, 4 free)
   e   extended (container for logical partitions)
Select (default p): p
Partition number (1-4, default 1):
First sector (1-127, default 1):
Last sector, +sectors or +size{K,M,G,T,P} (1-127, default 127): +4000G
Value out of range.
Last sector, +sectors or +size{K,M,G,T,P} (1-127, default 127):

---

### Post by weatherman2 on 2016-08-18
I have no idea how to clear the drive.  In any case - I'd start over, because you will need to create at least one partition anyway.

First, you will need to create a partition table.  Make sure it is a GPT partition table not the old MSDOS style, if you want to see the whole 4TB of the drive (otherwise you will be stuck at about 2.1 TB).  If there's already an MSDOS partition table, wipe it out and replace it with a GPT partition tbale.

Then create at least one partition.  The easiest may be a single 4TB ext4 partition table, as long as you'll never use the drive in Windows again.  If there's any reason you might want to use the drive in Windows again, create at least one NTFS partition.  You won't be able to use the ext4 partition in Windows (unless the "Ubuntu in Windows 10" thing which I haven't used yet will allow that).

It sounds like your Ubuntu server without a Gui?  If you have a Gui (mouse interface), install Gparted to make all of this very easy.  I'm not sure of the parted commands you need to create a partition table, etc. then format a partition as ext4; I always do it with Gparted because it's so much easier.  You can even boot a live USB of Ubuntu to do this if you don't have a machine that has a Gui interface.

---

### Post by pappo2 on 2016-08-18
I moved the Seagate back over to my Windows 10 PC and I can see all the files as if I never touched it with Linux.
My attempts using parted and fdisk, although they said they deleted the partition, never changed the drive.

Maybe my best bet is to figure out how to see it in Ubuntu and not try a reformat.

Any ideas on how to use Seagate Backup Plus drives in Ubuntu ?

Thanks for all your help

---

### Post by mhoffmanndk on 2017-02-28
Hi

Did you managed to mount your seagate device in ubuntu?

I found a solution yesterday....I used fuseext2 to mount

fuseext2 -o ro /dev/mapper/vg1-lv1 /mnt/seagate

Afterwards I was able to "ls" my seagate directory and use the rsync command to copy files onto another sata harddrive.

If I tried other simple commands like "df" or "ls -l", the terminal got stuck and had to kill it.

My plan are to copy my seagate content to another harddrive, then delete all partitions on the seagate device and create one 4Tb partition which can be available to both ubuntu and windows

---

### Post by RichTheCoder on 2017-09-14
Just thought I'd add my own experience to this thread. I too added a Seagate 4TB Backup Plus drive to my Ubuntu 16.04 system (running on a creaky old Dell with USB 2.0). 
Nautilus immediately mounted a partition named "Seagate Backup Plus Drive". "Disks" utility showed that it was the second partition on the disk, /dev/sdd2, it had NTFS files, and it occupied almost all the space except a tiny first partition (134MB).  Disks showed the first , /dev/sdd1 , was Partition Type "Microsoft Reserved" and Contents "Unknown".  
The command
sudo blkid 
provoked a complaint that "Partition 1 does not start on physical sector boundary. ", in the output for sdd .  This must be the odd Windows Reserved disk. 
Since I dual-boot with Windows 10 (for iTunes) I decided to leave the tiny partition alone. I expect never to mount it in Linux. 
gparted had no problem with the next steps : shrink the second partition , and, create a third partition in the empty space with ext4 filesystem . 
gparted only would create  a primary partition. The "Extended" option was greyed-out.

---

