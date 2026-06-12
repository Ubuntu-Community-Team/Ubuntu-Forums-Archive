---
title: "trim, partitions and running out of disk space"
date: 2011-07-15
forum: Hardware
---

### Post by PsYcHoTiC_MaDmAn on 2011-07-15
specifics.

Crucial C300 64GB set up as 

SDA1 : NTFS : 100 MiB System Reserved (flagged boot)
SDA2 : NTFS : 39.45 GiB (win 7 install)
SDA3 : extended : 20.07 GiB
SDA5 : EXT4 : 5.72 GiB : mount point /
SDA6 : linux swap : 1.91 GiB
SDA7 : EXT4 : 12.44 GiB : mount point /home


just had this message show up

>  Low Disk Space
the volume "Filesystem root" has only 152.2 MB disk space remaining.

also, gparted (and via examine) shows /home usage as 4.51GiB, however places only shows 2.1GiB

thought with the newer kernel that trim would automatically be on, however I can only explain the disk usage by trim not working. 

looking up several guides I've modified /etc/fstab so it has the entries

> # /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda5 during installation
UUID=564a4cbc-3d0f-404e-8b28-55712b864209 /               ext4    discard,noatime,nodiratime,errors=remount-ro 0       1
# /home was on /dev/sda7 during installation
UUID=d58bc421-8033-4de3-b2d7-6644d8df4017 /home           ext4    defaults        0       2
# swap was on /dev/sda6 during installation
UUID=c9c5d1ac-9397-4b65-b58e-b6805e6ed03d none            swap    sw              0       0
# swap was on /dev/sdb6 during installation
UUID=1a46c468-ea44-41f9-bd11-22245563ba41 none            swap    sw              0       0
tmpfs /tmp tmpfs defaults,noatime,mode=1777 0 0

haven't rebooted yet (want to finish watching my film.) what I'm wondering is will this clear the lot, or do I need to reinstall setting it up with trim to begin with (puzzled as to why there is a swap file, as I wanted that on the hard disk, and with 8GB I didn't feel it was needed

---

### Post by Blasphemist on 2011-07-15
> **PsYcHoTiC_MaDmAn said:**
> specifics.

Crucial C300 64GB set up as 

SDA1 : NTFS : 100 MiB System Reserved (flagged boot)
SDA2 : NTFS : 39.45 GiB (win 7 install)
SDA3 : extended : 20.07 GiB
SDA5 : EXT4 : 5.72 GiB : mount point /
SDA6 : linux swap : 1.91 GiB
SDA7 : EXT4 : 12.44 GiB : mount point /home


just had this message show up



also, gparted (and via examine) shows /home usage as 4.51GiB, however places only shows 2.1GiB

thought with the newer kernel that trim would automatically be on, however I can only explain the disk usage by trim not working. 

looking up several guides I've modified /etc/fstab so it has the entries



haven't rebooted yet (want to finish watching my film.) what I'm wondering is will this clear the lot, or do I need to reinstall setting it up with trim to begin with (puzzled as to why there is a swap file, as I wanted that on the hard disk, and with 8GB I didn't feel it was needed

Well I'm confused. This adds up to more than 64GB for one. If you're saying you have 8 GB of memory, then you might as well delete swap using GParted since it is so small. I can't tell from this where it is located on the drive but you may be able to use GParted to expand / to include the space from the deleted swap.

---

### Post by PsYcHoTiC_MaDmAn on 2011-07-15
> **Blasphemist said:**
> Well I'm confused. This adds up to more than 64GB for one. If you're saying you have 8 GB of memory, then you might as well delete swap using GParted since it is so small. I can't tell from this where it is located on the drive but you may be able to use GParted to expand / to include the space from the deleted swap.

SDA 5, 6 & 7 are all part of SDA 3

yeah, I can expand / into swap space,

anyway, film has rebooted, so going to try a restart to see if it clears space

ok. rebooted, and the file usage is down a little (5.06GiB instead of 5.5GiB) for /

however, still leaves me with a stupidly full drive. is there a command to force garbage collection

---

### Post by Blasphemist on 2011-07-15
Not a command that I know of. There is computer janitor in the software center and I would do what we've discussed.

---

### Post by PsYcHoTiC_MaDmAn on 2011-07-15
well I'm transferring my stuff off the home partition (as thats full of crap as well) (total data backed up 1.3GB, gparted shows 4.5GB used ( found the culprit, .dvdcss, sucked up 3.4GB. however deleting it has resulted in an increase in file usage in gparted....)

yay, a day of of downloads, install and config....

ubuntu shows it as a SSD under disk utility, if it knows that wtf doesn;t it automatically put TRIM on....

---

### Post by oldfred on 2011-07-15
With a small root like you have you need to regularly houseclean.

HOWTO: Recover Lost Disk Space - drs305
[http://ubuntuforums.org/showthread.php?t=1122670](http://ubuntuforums.org/showthread.php?t=1122670)
HOWTO: Cleaning up all those unnecessary junk files...
[http://ubuntuforums.org/showthread.php?t=140920](http://ubuntuforums.org/showthread.php?t=140920)
    Caution deborphan will delete anything you manually installed. See comment:
Better to use Synaptic to select the ones you no longer want. Also you get notified about dependencies to be removed and can reconsider, if need be.

HouseKeeping:
sudo apt-get update #resync package index
sudo apt-get upgrade #newest versions of all packages, update must be run first
sudo apt-get autoremove  #removes depenancies no longer needed
# removes .deb
sudo apt-get autoclean   # only removes files that cannot be downloaded anymore (obsolete)
Sometimes this does more?
sudo apt-get dist-upgrade  #updates dependancies

# empty trash
# remove log files if no issues
cd /var/log
sudo rm -f messages.*
sudo rm -v /var/log/*.gz

 How To: Disk Full? - Check Your Trash 
[http://ubuntuforums.org/showthread.php?t=898573](http://ubuntuforums.org/showthread.php?t=898573)

---

