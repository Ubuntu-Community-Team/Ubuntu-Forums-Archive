---
title: "Installed a New Harddrive and have Guid at the Mount Point?"
date: 2015-07-17
forum: Hardware
---

### Post by Nathan_Veysey on 2015-07-17
Hello New to Ubuntu

Ive installed a Drive and the Mount point is defined as /media/nathan/<Annoying GUID - asdasf-asfasf4 etc ... >  Mounted at /media/nathan/cc161d5b-8d48-4392-8620-0df4f49a87f2

I can navigate to /media/nathan/ and create directories, however through the GUI opening the Drive points me to the GUID location, is there some way I can change this? I&#8217;m attempting to set-up a mercurial server and would like some visual prompts on the server yet do not want to have to navigate to the GUID folder, or have to ever try and type that in? 

Ive also begun to create a directory at that location /media/nathan/mercurial/ - is that a bad idea for any reason? Don't completely understand the mounts concept at this stage and why there is a number of levels above the apparent Root or Mount point?

Thank you

---

### Post by oldfred on 2015-07-17
In Windows mounts are automatically c: or d: etc.
But in Linux you usually have to create a mount, but can have any name/label you like so it can be more informative than d:.

You may also have to create ownership & permissions, which is one of the main security features of Linux that Windows does not use.

For internal drive partitions, best to automatically mount with fstab. Then when you reboot they automatically are mounted. And if an external drive or a partition you only occasionally use best to add labels so it mounts with label instead of UUID. I add labels when I create a partition with gparted. Or when I forget or change something I use Disks to change labels. You can also use command line.

       Understanding fstab
[http://www.psychocats.net/ubuntu/mountlinux](http://www.psychocats.net/ubuntu/mountlinux)
[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)
[URL="https://wiki.archlinux.org/index.php/Fstab"]https://wiki.archlinux.org/index.php/Fstab
[/URL]
 [http://ubuntuforums.org/showthread.php?t=1983336](http://ubuntuforums.org/showthread.php?t=1983336)
Mount & edit fstab from user Morbius1 in Post # 6 - suggest using templates instead.
Good example of manually mounting, except I prefer /mnt/xxx as location to mount to.

[URL="https://wiki.archlinux.org/index.php/Fstab"]
[/URL]

---

### Post by weatherman2 on 2015-07-18
> **Nathan_Veysey said:**
> I can navigate to /media/nathan/ and create directories, however through the GUI opening the Drive points me to the GUID location, is there some way I can change this?

Install the program called Gparted - a partition manager for Linux.  (Perhaps it is already installed - not sure.)  Then start it up.   Find the new partition and create a Label for it.  Let's say you make the label "Data."  Reboot, then next time you mount that partition it will show up as /media/nathan/Data instead of the UUID.

(Just to be clear, you don't mount "drives" in Ubuntu, you mount partitions.  Your new hard drive may have only one large partition, but you still are mounting that one partition.  That's important to understand when you are using Gparted.)

> **Nathan_Veysey said:**
> Ive also begun to create a directory at that location /media/nathan/mercurial/ - is that a bad idea for any reason? Don't completely understand the mounts concept at this stage and why there is a number of levels above the apparent Root or Mount point?

Well, until you mount a partition, the directory you have created called "/media/nathan/mercurial" is just another directory on the OS (root) partition on your main hard drive, using up more space on it.  In Linux, you mount a partition in your file system in almost any directory you want.  You could mount your new hard drive's big partition there (using the "mount" command in a terminal for example) if you wanted to, but then any files you had already created in "/media/nathan/mecrurial" would become invisible - replaced (while mounted) with the new partition's files.

---

### Post by Nathan_Veysey on 2015-07-19
> **oldfred said:**
> In Windows mounts are automatically c: or d: etc.
But in Linux you usually have to create a mount, but can have any name/label you like so it can be more informative than d:.

You may also have to create ownership & permissions, which is one of the main security features of Linux that Windows does not use.

For internal drive partitions, best to automatically mount with fstab. Then when you reboot they automatically are mounted. And if an external drive or a partition you only occasionally use best to add labels so it mounts with label instead of UUID. I add labels when I create a partition with gparted. Or when I forget or change something I use Disks to change labels. You can also use command line.

       Understanding fstab
[http://www.psychocats.net/ubuntu/mountlinux](http://www.psychocats.net/ubuntu/mountlinux)
[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)
[URL="https://wiki.archlinux.org/index.php/Fstab"]https://wiki.archlinux.org/index.php/Fstab
[/URL]
 [http://ubuntuforums.org/showthread.php?t=1983336](http://ubuntuforums.org/showthread.php?t=1983336)
Mount & edit fstab from user Morbius1 in Post # 6 - suggest using templates instead.
Good example of manually mounting, except I prefer /mnt/xxx as location to mount to.

[URL="https://wiki.archlinux.org/index.php/Fstab"]
[/URL]

Thank you, starting to get my head around the different logic

Ok so I removed the previous Partition, and started again from gParted

Device is /dev/sdb1
The Mount Point is now /mnt/Development (I must have left the label field empty on the first pass) - Ive mounted as Ext4 (Version 1.0) - was mentioned as the preferred type in the instructions I found online. 

I have to physically mount this after booting (Mount On > /mnt/Development), and it creates an error when booting which asks me to skip or help. - Ill get the error and post shortly? 

Any ideas on what is causing that? Could it be something to do with Permissions here:
You may also have to create ownership & permissions, which is one of  the main security features of Linux that Windows does not use.

---

### Post by Nathan_Veysey on 2015-07-19
Thank you - Yes there&#8217;s definitely a new folder mercurial on the root partition - will make sure this is working correctly before continuing. Ill have to do some reading on Linux partitions, its created a whole bunch I wasn't aware on the install.

---

### Post by oldfred on 2015-07-19
Post these:
       sudo blkid -o list
sudo parted -l
       cat /etc/fstab

You create mount points like /mnt/Development or /mnt/data. Then you tell system which partition is that mount point. And what ownership & permissions that partition/mount has.

I have added labels like Data and mounts like /mnt/data. And then gotten confused since data and Data in Linux are two totally different labels/mounts/names. Case is important.

---

### Post by Nathan_Veysey on 2015-07-20
The error in Boot is:
[IMG]http://i1029.photobucket.com/albums/y357/Nathan_Peter_Veysey/IMG_20150720_170252.jpg_zpsfomysmbk.png[/IMG]

---

### Post by Nathan_Veysey on 2015-07-20
Heres that information OldFred[B]

~$ sudo blkid -o list[/B]
device     fs_type label    mount point    UUID
-------------------------------------------------------------------------------
/dev/sda1  ext2             /boot          5c929586-b1df-48c2-91fa-b0740cee5ba8
/dev/sda5  LVM2_member      (in use)       Eg9rK3-bbZB-JJwF-qNbU-Fqfk-ZOCw-5JadfJ
**/dev/sdb1  ext4    Development (not mounted) be136dc6-482c-4a8c-b50b-d397cc255af6**
/dev/mapper/ubuntu--vg-root
           ext4             /              0dd394c3-cd09-4154-a06f-7be2734a86ac
/dev/mapper/ubuntu--vg-swap_1
           swap             <swap>         7f62e466-6277-4084-a2d6-3360c36f8ff5


**~$ sudo parted -l**
Model: ATA ST1000DX001-1CM1 (scsi)
Disk /dev/sda: 1000GB
Sector size (logical/physical): 512B/4096B
Partition Table: msdos

Number  Start   End     Size    Type      File system  Flags
 1      1049kB  256MB   255MB   primary   ext2         boot
 2      257MB   1000GB  1000GB  extended
 5      257MB   1000GB  1000GB  logical                lvm

[B]
Model: ATA WDC WD6400AAKS-2 (scsi)[/B]
[B]Disk /dev/sdb: 640GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End    Size   Type     File system  Flags
 1      1049kB  640GB  640GB  primary  ext4
[/B]

Model: Linux device-mapper (linear) (dm)
Disk /dev/mapper/ubuntu--vg-root: 974GB
Sector size (logical/physical): 512B/4096B
Partition Table: loop

Number  Start  End    Size   File system  Flags
 1      0.00B  974GB  974GB  ext4


Model: Linux device-mapper (linear) (dm)
Disk /dev/mapper/ubuntu--vg-swap_1: 25.7GB
Sector size (logical/physical): 512B/4096B
Partition Table: loop

Number  Start  End     Size    File system     Flags
 1      0.00B  25.7GB  25.7GB  linux-swap(v1)

**~$ cat /etc/fstab**
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
/dev/mapper/ubuntu--vg-root /               ext4    errors=remount-ro 0       1
# /boot was on /dev/sda1 during installation
UUID=5c929586-b1df-48c2-91fa-b0740cee5ba8 /boot           ext2    defaults        0       2
/dev/mapper/ubuntu--vg-swap_1 none            swap    sw              0       0
LABEL=Development /mnt/Development auto nosuid,nodev,nofail,x-gvfs-show 0 0

---

### Post by oldfred on 2015-07-20
I think it is a missing comma. auto is one of the parameters, so needs a comma after it. Otherwise you then have too many settins in entry.

auto nosuid,nodev,nofail,x-gvfs-show

If you click on it in Nautilus file manager, do it mount ok under the label?

---

### Post by Nathan_Veysey on 2015-07-23
Cheers will check the comma.

---

### Post by Nathan_Veysey on 2015-07-23
Cheers will check the comma.

---

### Post by Nathan_Veysey on 2015-07-23
Cheers will check the comma.

---

### Post by Nathan_Veysey on 2015-07-23
> **oldfred said:**
> I think it is a missing comma. auto is one of the parameters, so needs a comma after it. Otherwise you then have too many settins in entry.

auto nosuid,nodev,nofail,x-gvfs-show

If you click on it in Nautilus file manager, do it mount ok under the label?

I added in a comma into the fstab file and that forces Disks to load the information incorrectly into the GUI interface.
Attempting to load the data. So I renamed the label as was continuing to encounter errors, changed from Development to Dev.

Generated from Disks - Auto corresponds to file system type by my understanding, which Ive attempted to set AS ext4 and Ext4 also incase of Case.
/dev/disk/by-uuid/cca26d6d-be09-453e-91f4-5266f4dc25f3 Dev auto nosuid,nodev,nofail,x-gvfs-show 0 0  

When I try and mount the disk manually I encounter this error now - which I wasn't previously, but really need it to auto mount.
Error mounting system-managed device /dev/sdb1: Command-line `mount "Dev"' exited with non-zero exit status 32: mount: wrong fs type, bad option, bad superblock on /dev/sdb1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

---

### Post by weatherman2 on 2015-07-23
You need a / in front of "Dev":

```

/dev/disk/by-uuid/cca26d6d-be09-453e-91f4-5266f4dc25f3 /Dev auto nosuid,nodev,nofail,x-gvfs-show 0 0 

```

If you have created a directory called "/Dev" .  If you meant "/mnt/Dev" then your line would be:

```

/dev/disk/by-uuid/cca26d6d-be09-453e-91f4-5266f4dc25f3 /mnv/Dev auto nosuid,nodev,nofail,x-gvfs-show 0 0 

```

---

### Post by oldfred on 2015-07-23
You have to create a mount point like /mnt/data. You Dev is not a mount point. Perhaps /Dev is but then that would be in / (root). Usually /mnt or media are used.

 [http://ubuntuforums.org/showthread.php?t=1983336](http://ubuntuforums.org/showthread.php?t=1983336)
Mount & edit fstab from user Morbius1 in Post # 6 - suggest using templates instead.
Good example of manually mounting, except I prefer /mnt/xxx as location to mount to.

There is no Ext4, just ext4. Sorry, the auto may be correct, I have always use correct type.
       sudo mkdir /mnt/Development
     LABEL=Development /mnt/Development ext4 defaults,noatime 0 2


 ** And when you are done editing fstab and saving it run the following command to test for errors and mount the partitions without requiring a reboot. You will know before you reboot if something is amiss. Make sure you have partition unmounted if previously mounted:
sudo mount -a

---

### Post by weatherman2 on 2015-07-24
To add to what OldFred said: the "sudo mount -a" command succeeded (no errors) when IT GIVES NO OUTPUT.  If there is a problem with your /etc/fstab file, it will give you an error.  That's a little confusing (that "no output" means everything is good) if you're new to it.

---

### Post by Nathan_Veysey on 2015-07-24
> **weatherman2 said:**
> To add to what OldFred said: the "sudo mount -a" command succeeded (no errors) when IT GIVES NO OUTPUT.  If there is a problem with your /etc/fstab file, it will give you an error.  That's a little confusing (that "no output" means everything is good) if you're new to it.

Hello, 

Thank you for your help, Im starting to get a good grasp on whats going on, but still cant solve the issue. 

I’ve checked the commands, and modified to mount to /mnt/Dev/ - It creates the folder then throughs and exception (I removed the previous folders in there to test)

I think the fstab file may be correct?

# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
/dev/mapper/ubuntu--vg-root /               ext4    errors=remount-ro 0       1
# /boot was on /dev/sda1 during installation
UUID=5c929586-b1df-48c2-91fa-b0740cee5ba8 /boot           ext2    defaults        0       2
/dev/mapper/ubuntu--vg-swap_1 none            swap    sw              0       0

#/dev/disk/by-uuid/1030939a-376f-4cc9-92a6-a19bd3b6785b Development  nosuid,nodev,nofail,x-gvfs-show 0 0
[B]/dev/disk/by-uuid/cca26d6d-be09-453e-91f4-5266f4dc25f3 /mnt/Dev auto nosuid,nodev,nofail,x-gvfs-show 0 0
[/B]
So typing this, or trying to mount through the file browser causes errors.

[B]sudo mount -a

mount: wrong fs type, bad option, bad superblock on /dev/sdb1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so
[/B]
The Drive is formatted as Ext4.0  - Ive tried a few instructionals on how to do this but not sure what I’ve done wrong. I’ve updated the fstab file to 
**/dev/sdb1 /mnt/Dev ext4 nosuid,nodev,nofail,x-gvfs-show 0 0**

Same error, still

**$ parted -l**
Model: ATA ST1000DX001-1CM1 (scsi)
Disk /dev/sda: 1000GB
Sector size (logical/physical): 512B/4096B
Partition Table: msdos

Number  Start   End     Size    Type      File system  Flags
 1      1049kB  256MB   255MB   primary   ext2         boot
 2      257MB   1000GB  1000GB  extended
 5      257MB   1000GB  1000GB  logical                lvm


[B]Model: ATA WDC WD6400AAKS-2 (scsi)
Disk /dev/sdb: 640GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End    Size   Type     File system  Flags
 1      1049kB  640GB  640GB  primary  ext4
[/B]

Model: Linux device-mapper (linear) (dm)
Disk /dev/mapper/ubuntu--vg-swap_1: 25.7GB
Sector size (logical/physical): 512B/4096B
Partition Table: loop

Number  Start  End     Size    File system     Flags
 1      0.00B  25.7GB  25.7GB  linux-swap(v1)


Model: Linux device-mapper (linear) (dm)
Disk /dev/mapper/ubuntu--vg-root: 974GB
Sector size (logical/physical): 512B/4096B
Partition Table: loop

Number  Start  End    Size   File system  Flags
 1      0.00B  974GB  974GB  ext4


Ive run 

**:~# e2fsck -f /dev/sdb1**

From [http://www.cyberciti.biz/tips/surviving-a-linux-filesystem-failures.html](http://www.cyberciti.biz/tips/surviving-a-linux-filesystem-failures.html)

[B]e2fsck 1.42.9 (4-Feb-2014)
Pass 1: Checking inodes, blocks, and sizes
Pass 2: Checking directory structure
Pass 3: Checking directory connectivity
Pass 4: Checking reference counts
Pass 5: Checking group summary information
Dev: 11/39075840 files (0.0% non-contiguous), 2503004/156282624 blocks

[/B]

mke2fs -n /dev/sdb1
[B]mke2fs 1.42.9 (4-Feb-2014)
Filesystem label=
OS type: Linux
Block size=4096 (log=2)
Fragment size=4096 (log=2)
Stride=0 blocks, Stripe width=0 blocks
39075840 inodes, 156282624 blocks
7814131 blocks (5.00%) reserved for the super user
First data block=0
Maximum filesystem blocks=4294967296
4770 block groups
32768 blocks per group, 32768 fragments per group
8192 inodes per group
Superblock backups stored on blocks: 
    32768, 98304, 163840, 229376, 294912, 819200, 884736, 1605632, 2654208, 
    4096000, 7962624, 11239424, 20480000, 23887872, 71663616, 78675968, 
    102400000[/B]

Which file system type should it be? I wouldn't have assumed the Filesystem type would have mattered? and read somewhere that ext4 was good. Ive attempted to remove, format and recreate the partitions but still has issues? Is the disk done? or is there some reasonable explanation for this issue?

** sudo mkfs.ext4 /dev/sdb1 **

Doesn't work either, still a bad superblock lost my label - but thats no biggy.

Any ideas? Would it be worth me trying another HDD - have another spare there...

---

### Post by oldfred on 2015-07-24
I might in Disks click on icon in upper right corner. It has Smart Status and see what it says about drive. I do not know details, but it needs to say passed.

The ext4 is the standard now for Ubuntu format. I use it for my data partitions all the time. I normally use gparted to partition & format.

       [http://linuxexpresso.wordpress.com/2010/03/31/repair-a-broken-ext4-superblock-in-ubuntu/](http://linuxexpresso.wordpress.com/2010/03/31/repair-a-broken-ext4-superblock-in-ubuntu/)
Remove first inode to use alternative superblock:
[http://ubuntuforums.org/showthread.php?t=1682038](http://ubuntuforums.org/showthread.php?t=1682038)
Using alternative superblock to check ext3
[http://planet.admon.org/using-alternative-superblock-to-check-ext3/](http://planet.admon.org/using-alternative-superblock-to-check-ext3/)
List backup superblocks:
sudo dumpe2fs /dev/sda5 | grep -i backup
then use backup superblock, 32768 just an example, try several
sudo fsck -b 32768 /dev/sda5

---

### Post by weatherman2 on 2015-07-24
Change your line in /etc/fstab from

```
/dev/sdb1 /mnt/Dev ext4 nosuid,nodev,nofail,x-gvfs-show 0 0
```

to this one with fewer options:

```
/dev/sdb1 /mnt/Dev ext4 rw 0 0
```



And try the "sudo mount -a" command again.

---

### Post by Nathan_Veysey on 2015-07-29
> **weatherman2 said:**
> Change your line in /etc/fstab from

```
/dev/sdb1 /mnt/Dev ext4 nosuid,nodev,nofail,x-gvfs-show 0 0
```

to this one with fewer options:

```
/dev/sdb1 /mnt/Dev ext4 rw 0 0
```



And try the "sudo mount -a" command again.

Hello Weatherman, 
Sorry for the delay been working on a deadline project. I Tried that, 

~$ sudo mount -a
mount: wrong fs type, bad option, bad superblock on /dev/sdb1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

Still the same error

---

### Post by Nathan_Veysey on 2015-07-29
> **oldfred said:**
> I might in Disks click on icon in upper right corner. It has Smart Status and see what it says about drive. I do not know details, but it needs to say passed.

The ext4 is the standard now for Ubuntu format. I use it for my data partitions all the time. I normally use gparted to partition & format.

       [http://linuxexpresso.wordpress.com/2010/03/31/repair-a-broken-ext4-superblock-in-ubuntu/](http://linuxexpresso.wordpress.com/2010/03/31/repair-a-broken-ext4-superblock-in-ubuntu/)
Remove first inode to use alternative superblock:
[http://ubuntuforums.org/showthread.php?t=1682038](http://ubuntuforums.org/showthread.php?t=1682038)
Using alternative superblock to check ext3
[http://planet.admon.org/using-alternative-superblock-to-check-ext3/](http://planet.admon.org/using-alternative-superblock-to-check-ext3/)
List backup superblocks:
sudo dumpe2fs /dev/sda5 | grep -i backup
then use backup superblock, 32768 just an example, try several
sudo fsck -b 32768 /dev/sda5


Disk status shows as OK for all assessments, (1 Year run Time)
Last self-test completed successfully
Threshold not exceeded
Disk is OK, 65 bad sectors

The Primary HDD shows as No bad Sectors however. (1 Day Run Time total) - Have had no need to leave running so far.


Ill check out the other options,

---

### Post by weatherman2 on 2015-07-29
Forgive me - it's been a few days and I've lost track of what you've tried and what works and doesn't, and I don't have time to re-read the whole thread at this moment.

Does this work?

```
sudo mount /dev/sdb1 /mnt
```

?

If not, then forget about /etc/fstab - no combination of options will work, you've got some other problem.

"Bad sectors" could mean several things, that's kind of a generic summary.  To get more information, I use GSmartControl (or the terminal-based smartctl command, part of smartmontools) to see current S.M.A.R.T. attributes.

You might try this:

```

sudo apt-get update
sudo apt-get install smartmontools
sudo smartctl -A -d sat /dev/sdb

```

That last line should give you output of numerous lines - Attributes.  If so, filter it like this:

```

sudo smartctl -A -d sat /dev/sdb | grep -i sector

```

and give the output (should be just two or three lines) here.  65 Pending Sectors would be really bad.  65 Reallocated Sectors would mean a lot of sectors have failed have been replaced with spares so the disk is technically still usable (but I wouldn't use it for long).  If you have something like 65 Reallocation Events or something, they may be false errors.

---

### Post by Nathan_Veysey on 2015-08-06
> **weatherman2 said:**
> Forgive me - it's been a few days and I've lost track of what you've tried and what works and doesn't, and I don't have time to re-read the whole thread at this moment.

Does this work?

```
sudo mount /dev/sdb1 /mnt
```

?

If not, then forget about /etc/fstab - no combination of options will work, you've got some other problem.

"Bad sectors" could mean several things, that's kind of a generic summary.  To get more information, I use GSmartControl (or the terminal-based smartctl command, part of smartmontools) to see current S.M.A.R.T. attributes.

You might try this:

```

sudo apt-get update
sudo apt-get install smartmontools
sudo smartctl -A -d sat /dev/sdb

```

That last line should give you output of numerous lines - Attributes.  If so, filter it like this:

```

sudo smartctl -A -d sat /dev/sdb | grep -i sector

```

and give the output (should be just two or three lines) here.  65 Pending Sectors would be really bad.  65 Reallocated Sectors would mean a lot of sectors have failed have been replaced with spares so the disk is technically still usable (but I wouldn't use it for long).  If you have something like 65 Reallocation Events or something, they may be false errors.

Thank you Weatherman2 , clearing skies. 

sudo mount /dev/sdb1 /mnt 

Did work, so updated the fstab entry to 
/dev/sdb1 /mnt/Dev auto rw 0 0

Removed the extra Gui related (?) commands from the fstab entry and is mounting on Boot, and is available in the Gui at the mount point,

Thank you.

---

