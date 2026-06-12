---
title: "mdadm raid 1 not staying in after reboot"
date: 2009-07-07
forum: Installation &amp; Upgrades
---

### Post by n5oe on 2009-07-07
I am a new user somewhat with Ubuntu 9.04 Desktop and new to this forum, I hope this goes correctly. I am having some issues getting mdadm for raid 1 or even raid 0 for that fact to work properly. I have a small server up and running now for about a year. I have the need for a raid1 setup for storage on this server. I currently have the main OS installed on a single 60G SATA HD, and have now installed 2 -1TB SATA drives that I wish to put into Raid1 for storage of files, data, and pictures for all the users.

I have followed this link [http://beginlinux.com/server_training/server-managment-topics/999-raid-0-on-ubuntu-804](http://beginlinux.com/server_training/server-managment-topics/999-raid-0-on-ubuntu-804) 
trying both the raid0 and with raid1 options over the last couple of nights. The raid will build and mount on a /raid directory that I created, I can write and read to the /dev/md0 mounted on /raid manually. However I did not create ahead of time the "raid aware partitions" not knowing how to go about this???

Here lies the problem, when I edit /etc/fstab with the following line
/dev/md0        /raid            auto   defaults        0       2
and reboot the array never comes back, either time with raid0 or raid1 setups.

I have tried sudo mdadm --assemble /dev/md0 /dev/sdc /dev/sdd
mdadm: device /dev/md0 already active - cannot assemble it
but it does not show under df -h, or will not come in with mount -a command

After a reboot I try this
sudo mdadm --query --detail /dev/md0
and get this mdadm: cannot open /dev/md0: No such file or directory

then this  sudo mdadm --assemble /dev/md0 /dev/sdc /dev/sdd
mdadm: cannot open device /dev/sdc: Device or resource busy

What am I missing here, do I need to partition the drives in gparted somehow? Use an Alternate CD and partition the TB drives? HOW To on both of these will be needed, tried it to some extent but still no luck

Thanks so much for the help ahead of time

################UPDATE##################

Last night I partitioned the drives as per this site using fdisk
[http://beginlinux.com/server_training/server-managment-topics/998-create-raid-on-ubuntu-804-part-1](http://beginlinux.com/server_training/server-managment-topics/998-create-raid-on-ubuntu-804-part-1)
Set as below in fdisk -l
Disk /dev/sdc: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x20d02769

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1      121601   976760001   fd  Linux raid autodetect

Disk /dev/sdd: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x20d02769

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1               1      121601   976760001   fd  Linux raid autodetect

Thes zeroed the superblocks as follows
n5oe@ubuntu-server:~$ sudo mdadm --zero-superblock /dev/sdc
n5oe@ubuntu-server:~$ sudo mdadm --zero-superblock /dev/sdd

Removed mdadm
n5oe@ubuntu-server:~$ sudo apt-get remove mdadm
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  jabber-common libcurl3
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  mdadm
0 upgraded, 0 newly installed, 1 to remove and 9 not upgraded.
After this operation, 676kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 157271 files and directories currently installed.)
Removing mdadm ...
 * Stopping MD monitoring service mdadm --monitor                                                                [ OK ] 
update-initramfs: deferring update (trigger activated)
Processing triggers for man-db ...
Processing triggers for doc-base ...
Processing 1 removed doc-base file(s)...
Registering documents with scrollkeeper...
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-2.6.28-13-generic

Rebooted the server and did a cat /proc/mdstatn5oe@ubuntu-server:~$ cat /proc/mdstat
Personalities : 
unused devices: <none>

Reinstalled mdadm
n5oe@ubuntu-server:~$ sudo apt-get install mdadm
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  jabber-common libcurl3
Use 'apt-get autoremove' to remove them.
The following NEW packages will be installed:
  mdadm
0 upgraded, 1 newly installed, 0 to remove and 9 not upgraded.
Need to get 0B/238kB of archives.
After this operation, 676kB of additional disk space will be used.
Preconfiguring packages ...
Selecting previously deselected package mdadm.
(Reading database ... 157244 files and directories currently installed.)
Unpacking mdadm (from .../mdadm_2.6.7.1-1ubuntu8_amd64.deb) ...
Processing triggers for doc-base ...
Processing 1 added doc-base file(s)...
Registering documents with scrollkeeper...
Processing triggers for man-db ...
Setting up mdadm (2.6.7.1-1ubuntu8) ...
Generating array device nodes... /var/lib/dpkg/info/mdadm.postinst: 170: /dev/MAKEDEV: not found
failed.
 Removing any system startup links for /etc/init.d/mdadm-raid ...
update-initramfs: deferring update (trigger activated)
 * Starting MD monitoring service mdadm --monitor                                                                [ OK ] 
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-2.6.28-13-generic


The restarted building the raid1 array
n5oe@ubuntu-server:~$ sudo mdadm --create /dev/md0 --level=1 --raid-devices=2 /dev/sdc /dev/sdd
mdadm: /dev/sdc appears to contain an ext2fs file system
    size=976762496K  mtime=Tue Jul  7 18:45:09 2009
mdadm: /dev/sdd appears to contain an ext2fs file system
    size=976762496K  mtime=Tue Jul  7 18:45:09 2009
mdadm: /dev/sdd appears to be part of a raid array:
    level=raid1 devices=2 ctime=Mon Jul  6 20:30:26 2009
Continue creating array? y
mdadm: array /dev/md0 started.

Did another car/proc/mdstat
n5oe@ubuntu-server:~$ cat /proc/mdstat
Personalities : [raid1] 
md0 : active raid1 sdd[1] sdc[0]
      976762496 blocks [2/2] [UU]
      [>....................]  resync =  0.5% (5416704/976762496) finish=152.3min speed=106262K/sec
      unused devices: <none>


All went well through the resync process and I did a detail listing and all looks well there,,
n5oe@ubuntu-server:/media$ sudo mdadm --detail /dev/md0
[sudo] password for n5oe: 
/dev/md0:
        Version : 00.90
  Creation Time : Tue Jul  7 20:11:34 2009
     Raid Level : raid1
     Array Size : 976762496 (931.51 GiB 1000.20 GB)
  Used Dev Size : 976762496 (931.51 GiB 1000.20 GB)
   Raid Devices : 2
  Total Devices : 2
Preferred Minor : 0
    Persistence : Superblock is persistent
    Update Time : Tue Jul  7 20:11:34 2009
          State : clean, resyncing
 Active Devices : 2
Working Devices : 2
 Failed Devices : 0
  Spare Devices : 0
 Rebuild Status : 40% complete
           UUID : 0aa891ef:93cd3da4:0308d362:1f0077d8 (local to host ubuntu-server)
         Events : 0.1
    Number   Major   Minor   RaidDevice State
       0       8       32        0      active sync   /dev/sdc
       1       8       48        1      active sync   /dev/sdd



Mounted the raid1 array and that went well too,

n5oe@ubuntu-server:/etc$ sudo mount /dev/md0 /media/1TBRaid1Array
n5oe@ubuntu-server:/etc$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1              55G   17G   35G  33% /
tmpfs                 930M     0  930M   0% /lib/init/rw
varrun                930M  600K  930M   1% /var/run
varlock               930M     0  930M   0% /var/lock
udev                  930M  168K  930M   1% /dev
tmpfs                 930M   76K  930M   1% /dev/shm
lrm                   930M  2.5M  928M   1% /lib/modules/2.6.28-13-generic/volatile
/dev/sdb1              57G   49G  5.2G  91% /media/60gBackup
/dev/sde1              56G  9.7G   43G  19% /media/60gBackup2
/dev/md0              917G  200M  871G   1% /media/1TBRaid1Array
n5oe@ubuntu-server:/etc$ sudo mdadm --detail /dev/md0
/dev/md0:
        Version : 00.90
  Creation Time : Tue Jul  7 20:11:34 2009
     Raid Level : raid1
     Array Size : 976762496 (931.51 GiB 1000.20 GB)
  Used Dev Size : 976762496 (931.51 GiB 1000.20 GB)
   Raid Devices : 2
  Total Devices : 2
Preferred Minor : 0
    Persistence : Superblock is persistent
    Update Time : Tue Jul  7 21:18:30 2009
          State : active, resyncing
 Active Devices : 2
Working Devices : 2
 Failed Devices : 0
  Spare Devices : 0
 Rebuild Status : 54% complete
           UUID : 0aa891ef:93cd3da4:0308d362:1f0077d8 (local to host ubuntu-server)
         Events : 0.3
    Number   Major   Minor   RaidDevice State
       0       8       32        0      active sync   /dev/sdc
       1       8       48        1      active sync   /dev/sdd

Once the resync completed I double checked the /etc/fstab to show as follows
# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda1 during installation
UUID=12187923-03a3-4b45-8b66-43c2d1c34bf0 /               ext3    relatime,errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=55182b8e-0ee4-4efc-b04a-42bc0d60ebf4 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/sdb1       /media/60gBackup auto   defaults        1       2
/dev/sde1       /media/60gBackup2 auto  defaults        1       2
/dev/md0        /media/1TBRaid1Array    auto    defaults        1       2

THEN rebooted the server again, done a cat /proc/mdstat and here is the PROBLEM again, the array fails to mount fully,,,
n5oe@ubuntu-server:~$  cat /proc/mdstat
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10] 
md0 : active raid1 sdd[1]
      976762496 blocks [2/1] [_U]
      md_d0 : inactive sdc[0](S)
      976762496 blocks
       unused devices: <none>

I then had to run this command to get 1/2 of the array back tht still holds some test data I put on it,,,
n5oe@ubuntu-server:~$ sudo mount -t ext3 /dev/sdc /media/1TBRaid1Array/
n5oe@ubuntu-server:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1              55G   17G   35G  33% /
tmpfs                 930M     0  930M   0% /lib/init/rw
varrun                930M  372K  930M   1% /var/run
varlock               930M     0  930M   0% /var/lock
udev                  930M  168K  930M   1% /dev
tmpfs                 930M     0  930M   0% /dev/shm
lrm                   930M  2.5M  928M   1% /lib/modules/2.6.28-13-generic/volatile
/dev/sdb1              57G   49G  5.2G  91% /media/60gBackup
/dev/sde1              56G  9.7G   43G  19% /media/60gBackup2
/dev/sdc              917G  336M  870G   1% /media/1TBRaid1Array


And here I am again, no Raid1 array, will not come in after reboot and have to manually install the partition to do anything,

Please help
Thanks

---

### Post by ronparent on 2009-07-08
Did you create the mount point /raid? The mount point in your file system must be created for the mount command to work.

---

### Post by n5oe on 2009-07-09
Yes, have tried with a mountpoit /raid and also a new one called /media/1TBRaid1Array

etc/fstab as follows
# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda1 during installation
UUID=12187923-03a3-4b45-8b66-43c2d1c34bf0 /               ext3    relatime,errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=55182b8e-0ee4-4efc-b04a-42bc0d60ebf4 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/sdb1       /media/60gBackup auto   defaults        1       2
/dev/sde1       /media/60gBackup2 auto  defaults        1       2
/dev/md0        /media/1TBRaid1Array    auto    defaults        1       2

This morning after a reboot I get this with /cat/proc/mdstat
n5oe@ubuntu-server:~$ cat /proc/mdstat
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10] 
unused devices: <none>

This after a working Radi1 array before reboot, mounted on /media/1TBraid1Array that I could write to and view just fine. There is no /etc/mdadm/mdadm.conf file now however????
So deep into confusion now I need to totally start from scratch somehow.
Thanks for the reply

---

### Post by Lampi on 2009-07-09
> **n5oe said:**
> There is no /etc/mdadm/mdadm.conf file now however????

well - you need this file ... /etc/mdadm.conf contains the arrays to be assembled on system startup.

"man mdadm.conf" should give you the idea how to set it up properly. 

There is a script called mkconf in /usr/share/mdadm helping you to recreate a proper config. Again: refer to the manpage of mdadm.conf to make sure you run it accordingly.

---

### Post by n5oe on 2009-07-10
OK after another wasted night and NO luck here is what I did,,, I removed everything I could think of, reinstalled and created a mdadm.conf file successfully thanks to the listing above. BUT it still did not mount upon a reboot,,, says 
> 
n5oe@ubuntu-server:~$ sudo mdadm -A /dev/md0
mdadm: no devices found for /dev/md0
n5oe@ubuntu-server:~$ cat /proc/mdstat
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10] 
md_d0 : inactive sdc[0](S)
      976762496 blocks
       
unused devices: <none>
n5oe@ubuntu-server:~$ sudo mdadm --assemble --scan
mdadm: no devices found for /dev/md0
/dev/md0: File exists
mdadm: /dev/md/0 has been started with 1 drive (out of 2).
n5oe@ubuntu-server:~$ fdisk -l
n5oe@ubuntu-server:~$ sudo fdisk-l
sudo: fdisk-l: command not found
n5oe@ubuntu-server:~$ sudo fdisk -l

Disk /dev/sda: 61.4 GB, 61492838400 bytes
255 heads, 63 sectors/track, 7476 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x90909090

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        7165    57552831   83  Linux
/dev/sda2            7166        7476     2498107+   5  Extended
/dev/sda5            7166        7476     2498076   82  Linux swap / Solaris

Disk /dev/sdb: 61.4 GB, 61492838400 bytes
255 heads, 63 sectors/track, 7476 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x43de2278

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        7476    60050938+  83  Linux

Disk /dev/sdc: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000

Disk /dev/sdc doesn't contain a valid partition table

Disk /dev/sdd: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000

Disk /dev/sdd doesn't contain a valid partition table

Disk /dev/sde: 60.0 GB, 60022480896 bytes
255 heads, 63 sectors/track, 7297 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x90909090

   Device Boot      Start         End      Blocks   Id  System
/dev/sde1               1        7297    58613121   83  Linux

Disk /dev/md0: 1000.2 GB, 1000204795904 bytes
2 heads, 4 sectors/track, 244190624 cylinders
Units = cylinders of 8 * 512 = 4096 bytes
Disk identifier: 0x00000000

Disk /dev/md0 doesn't contain a valid partition table
n5oe@ubuntu-server:~$ 
n5oe@ubuntu-server:~$ sudo mount /dev/sdd /media/1TBRaid1Array
[sudo] password for n5oe: 
mount: unknown filesystem type 'linux_raid_member'
n5oe@ubuntu-server:~$ sudo mount -t ext3 /dev/sdd /media/1TBRaid1Array
mount: /dev/sdd already mounted or /media/1TBRaid1Array busy
n5oe@ubuntu-server:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1              55G   17G   35G  33% /
tmpfs                 930M     0  930M   0% /lib/init/rw
varrun                930M  396K  930M   1% /var/run
varlock               930M     0  930M   0% /var/lock
udev                  930M  168K  930M   1% /dev
tmpfs                 930M     0  930M   0% /dev/shm
lrm                   930M  2.5M  928M   1% /lib/modules/2.6.28-13-generic/volatile
/dev/sdb1              57G   49G  5.2G  91% /media/60gBackup
/dev/sde1              56G  9.7G   43G  19% /media/60gBackup2And here is the LONG story on what I did tonight

sudo mdadm --stop /dev/md0
```
sudo mdadm --zero-superblock /dev/sdc
``````
sudo mdadm --zero-superblock /dev/sdd
``````
sudo rm /etc/mdadm/mdadm.conf
``````
sudo apt-get remove mdadm
```Then I fdisk the two drives, again, sdc and sdd. deleted the main partition that was on there, used "p" to verify that it was gone, and "w" to write changes to disk.

sudo fdisk -l at this point shows
> Disk /dev/sda: 61.4 GB, 61492838400 bytes
255 heads, 63 sectors/track, 7476 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x90909090

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        7165    57552831   83  Linux
/dev/sda2            7166        7476     2498107+   5  Extended
/dev/sda5            7166        7476     2498076   82  Linux swap / Solaris

Disk /dev/sdb: 61.4 GB, 61492838400 bytes
255 heads, 63 sectors/track, 7476 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x43de2278

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        7476    60050938+  83  Linux

Disk /dev/sdc: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xc195bcef

   Device Boot      Start         End      Blocks   Id  System

Disk /dev/sdd: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xc195bcef

   Device Boot      Start         End      Blocks   Id  System

Disk /dev/sde: 60.0 GB, 60022480896 bytes
255 heads, 63 sectors/track, 7297 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x90909090

   Device Boot      Start         End      Blocks   Id  System
/dev/sde1               1        7297    58613121   83  Linux


I then did a reboot and all was clean upon restart

Checked cat /proc/mdstat, looks clean
I then ran fdisk on drives sdc and sdd, created a new primary partition starting at first and going to last on the cylinders, set the system id to Linux-raid-auto by choosing "fd", and used "w"to write the chagnes to disk

Now ran fdisk -l to verify the following,
> n5oe@ubuntu-server:~$ sudo fdisk -l

Disk /dev/sda: 61.4 GB, 61492838400 bytes
255 heads, 63 sectors/track, 7476 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x90909090

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        7165    57552831   83  Linux
/dev/sda2            7166        7476     2498107+   5  Extended
/dev/sda5            7166        7476     2498076   82  Linux swap / Solaris

Disk /dev/sdb: 61.4 GB, 61492838400 bytes
255 heads, 63 sectors/track, 7476 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x43de2278

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        7476    60050938+  83  Linux

Disk /dev/sdc: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xc195bcef

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1      121601   976760001   fd  Linux raid autodetect

Disk /dev/sdd: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xc195bcef

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1               1      121601   976760001   fd  Linux raid autodetect

Disk /dev/sde: 60.0 GB, 60022480896 bytes
255 heads, 63 sectors/track, 7297 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x90909090

   Device Boot      Start         End      Blocks   Id  System
/dev/sde1               1        7297    58613121   83  Linux

Then ran the following to reinstall mdadm
```
sudo apt-get install mdadm

```I then created the raid1 array by issuing the following command
```
sudo mdadm --create /dev/md0 --level=1 --raid-devices=2 /dev/sdc /dev/sdd

```I know wanted to check the progress
> n5oe@ubuntu-server:~$ cat /proc/mdstat
Personalities : [raid1] 
md0 : active raid1 sdd[1] sdc[0]
      976762496 blocks [2/2] [UU]
      [>....................]  resync =  1.6% (16057024/976762496) finish=149.0min speed=107456K/sec
      
unused devices: <none>Now the big change tonight is I had a mdadm.conf file now that looks like this
> # mdadm.conf
#
# Please refer to mdadm.conf(5) for information about this file.
#

# by default, scan all partitions (/proc/partitions) for MD superblocks.
# alternatively, specify devices to scan, using wildcards if desired.
DEVICE partitions

# auto-create devices with Debian standard permissions
CREATE owner=root group=disk mode=0660 auto=yes

# automatically tag new arrays as belonging to the local system
HOMEHOST <system>

# instruct the monitoring daemon where to send mail alerts
MAILADDR root

# definitions of existing MD arrays
ARRAY /dev/md0 level=raid1 num-devices=2 UUID=76441269:12a5da71:5001eddb:97740a51

# This file was auto-generated on Thu, 09 Jul 2009 19:34:37 -0500
# by mkconf $Id$And now to create a file system on the assembled array
```
sudo mke2fs -j /dev/md0

```That completed and I successfully mounted the array, read and write working fine, SAMBA shares are fine
> n5oe@ubuntu-server:/etc/mdadm$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1              55G   17G   35G  33% /
tmpfs                 930M     0  930M   0% /lib/init/rw
varrun                930M  392K  930M   1% /var/run
varlock               930M     0  930M   0% /var/lock
udev                  930M  168K  930M   1% /dev
tmpfs                 930M     0  930M   0% /dev/shm
lrm                   930M  2.5M  928M   1% /lib/modules/2.6.28-13-generic/volatile
/dev/sdb1              57G   49G  5.2G  91% /media/60gBackup
/dev/sde1              56G  9.7G   43G  19% /media/60gBackup2
/dev/md0              917G  200M  871G   1% /media/1TBRaid1Array
Then after everything was working I verified once again with sudo mdadm --detail /dev/md0 and have the following
> n5oe@ubuntu-server:/etc/mdadm$ sudo mdadm --detail /dev/md0
[sudo] password for n5oe: 
/dev/md0:
        Version : 00.90
  Creation Time : Thu Jul  9 19:36:24 2009
     Raid Level : raid1
     Array Size : 976762496 (931.51 GiB 1000.20 GB)
  Used Dev Size : 976762496 (931.51 GiB 1000.20 GB)
   Raid Devices : 2
  Total Devices : 2
Preferred Minor : 0
    Persistence : Superblock is persistent

    Update Time : Thu Jul  9 22:57:42 2009
          State : active
 Active Devices : 2
Working Devices : 2
 Failed Devices : 0
  Spare Devices : 0

           UUID : 1e01989d:f27a728c:0308d362:1f0077d8 (local to host ubuntu-server)
         Events : 0.7

    Number   Major   Minor   RaidDevice State
       0       8       32        0      active sync   /dev/sdc
       1       8       48        1      active sync   /dev/sdd
My /etc/fstab looks like the following
> # /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda1 during installation
UUID=12187923-03a3-4b45-8b66-43c2d1c34bf0 /               ext3    relatime,errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=55182b8e-0ee4-4efc-b04a-42bc0d60ebf4 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/sdb1       /media/60gBackup auto   defaults        1       2
/dev/sde1       /media/60gBackup2 auto  defaults        1       2
/dev/md0        /media/1TBRaid1Array    auto    defaults        1       2OK NOW AFTER A REBOOT this is what I get, failure once again,
Here is my dmesg
> 
n5oe@ubuntu-server:~$ dmesg
[    0.000000] BIOS EBDA/lowmem at: 0009f000/0009f000
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.28-13-generic (buildd@yellow) (gcc version 4.3.3 (Ubuntu 4.3.3-5ubuntu4) ) #45-Ubuntu SMP Tue Jun 30 22:12:12 UTC 2009 (Ubuntu 2.6.28-13.45-generic)
[    0.000000] Command line: root=UUID=12187923-03a3-4b45-8b66-43c2d1c34bf0 ro quiet splash 
[    0.000000] KERNEL supported cpus:
[    0.000000]   Intel GenuineIntel
[    0.000000]   AMD AuthenticAMD
[    0.000000]   Centaur CentaurHauls
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f000 (usable)
[    0.000000]  BIOS-e820: 000000000009f000 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 0000000077ee0000 (usable)
[    0.000000]  BIOS-e820: 0000000077ee0000 - 0000000077ee3000 (ACPI NVS)
[    0.000000]  BIOS-e820: 0000000077ee3000 - 0000000077ef0000 (ACPI data)
[    0.000000]  BIOS-e820: 0000000077ef0000 - 0000000077f00000 (reserved)
[    0.000000]  BIOS-e820: 00000000e0000000 - 00000000f0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 0000000100000000 (reserved)
[    0.000000] DMI 2.4 present.
[    0.000000] Phoenix BIOS detected: BIOS may corrupt low RAM, working it around.
[    0.000000] last_pfn = 0x77ee0 max_arch_pfn = 0x3ffffffff
[    0.000000] Scanning 0 areas for low memory corruption
[    0.000000] modified physical RAM map:
[    0.000000]  modified: 0000000000000000 - 0000000000010000 (reserved)
[    0.000000]  modified: 0000000000010000 - 000000000009f000 (usable)
[    0.000000]  modified: 000000000009f000 - 00000000000a0000 (reserved)
[    0.000000]  modified: 00000000000f0000 - 0000000000100000 (reserved)
[    0.000000]  modified: 0000000000100000 - 0000000077ee0000 (usable)
[    0.000000]  modified: 0000000077ee0000 - 0000000077ee3000 (ACPI NVS)
[    0.000000]  modified: 0000000077ee3000 - 0000000077ef0000 (ACPI data)
[    0.000000]  modified: 0000000077ef0000 - 0000000077f00000 (reserved)
[    0.000000]  modified: 00000000e0000000 - 00000000f0000000 (reserved)
[    0.000000]  modified: 00000000fec00000 - 0000000100000000 (reserved)
[    0.000000] init_memory_mapping: 0000000000000000-0000000077ee0000
[    0.000000]  0000000000 - 0077e00000 page 2M
[    0.000000]  0077e00000 - 0077ee0000 page 4k
[    0.000000] kernel direct mapping tables up to 77ee0000 @ 10000-14000
[    0.000000] last_map_addr: 77ee0000 end: 77ee0000
[    0.000000] RAMDISK: 3781c000 - 37fefe38
[    0.000000] ACPI: RSDP 000F8210, 0024 (r2 ATI   )
[    0.000000] ACPI: XSDT 77EE3100, 004C (r1 ATI    ASUSACPI 42302E31 AWRD        0)
[    0.000000] ACPI: FACP 77EE8440, 00F4 (r3 ATI    ASUSACPI 42302E31 AWRD        0)
[    0.000000] FADT: X_PM1a_EVT_BLK.bit_width (8) does not match PM1_EVT_LEN (4)
[    0.000000] ACPI: DSDT 77EE3280, 515D (r1 ATI    ASUSACPI     1000 MSFT  3000000)
[    0.000000] ACPI: FACS 77EE0000, 0040
[    0.000000] ACPI: SSDT 77EE8680, 01C4 (r1 PTLTD  POWERNOW        1  LTP        1)
[    0.000000] ACPI: HPET 77EE88C0, 0038 (r1 ATI    ASUSACPI 42302E31 AWRD       98)
[    0.000000] ACPI: MCFG 77EE8940, 003C (r1 ATI    ASUSACPI 42302E31 AWRD        0)
[    0.000000] ACPI: APIC 77EE8580, 0084 (r1 ATI    ASUSACPI 42302E31 AWRD        0)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] (6 early reservations) ==> bootmem [0000000000 - 0077ee0000]
[    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
[    0.000000]   #1 [0000006000 - 0000008000]       TRAMPOLINE ==> [0000006000 - 0000008000]
[    0.000000]   #2 [0000200000 - 0000b7bbb0]    TEXT DATA BSS ==> [0000200000 - 0000b7bbb0]
[    0.000000]   #3 [003781c000 - 0037fefe38]          RAMDISK ==> [003781c000 - 0037fefe38]
[    0.000000]   #4 [000009f000 - 0000100000]    BIOS reserved ==> [000009f000 - 0000100000]
[    0.000000]   #5 [0000010000 - 0000012000]          PGTABLE ==> [0000010000 - 0000012000]
[    0.000000] found SMP MP-table at [ffff8800000f6560] 000f6560
[    0.000000]  [ffffe20000000000-ffffe20001bfffff] PMD -> [ffff880001200000-ffff880002dfffff] on node 0
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000010 -> 0x00001000
[    0.000000]   DMA32    0x00001000 -> 0x00100000
[    0.000000]   Normal   0x00100000 -> 0x00100000
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[2] active PFN ranges
[    0.000000]     0: 0x00000010 -> 0x0000009f
[    0.000000]     0: 0x00000100 -> 0x00077ee0
[    0.000000] On node 0 totalpages: 491119
[    0.000000]   DMA zone: 56 pages used for memmap
[    0.000000]   DMA zone: 2531 pages reserved
[    0.000000]   DMA zone: 1396 pages, LIFO batch:0
[    0.000000]   DMA32 zone: 6661 pages used for memmap
[    0.000000]   DMA32 zone: 480475 pages, LIFO batch:31
[    0.000000]   Normal zone: 0 pages used for memmap
[    0.000000]   Movable zone: 0 pages used for memmap
[    0.000000] Detected use of extended apic ids on hypertransport bus
[    0.000000] ACPI: PM-Timer IO Port: 0x4008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x02] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x03] disabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x02] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x03] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x04] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 4, version 0, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 low level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] ACPI: HPET id: 0x8200 base: 0xfed00000
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] SMP: Allowing 4 CPUs, 2 hotplug CPUs
[    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000f0000
[    0.000000] PM: Registered nosave memory: 00000000000f0000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at 78000000 (gap: 77f00000:68100000)
[    0.000000] PERCPU: Allocating 69632 bytes of per cpu data
[    0.000000] NR_CPUS: 64, nr_cpu_ids: 4, nr_node_ids 1
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 481871
[    0.000000] Kernel command line: root=UUID=12187923-03a3-4b45-8b66-43c2d1c34bf0 ro quiet splash 
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 32768 bytes)
[    0.000000] Fast TSC calibration using PIT
[    0.000000] Detected 1899.917 MHz processor.
[    0.004000] Console: colour VGA+ 80x25
[    0.004000] console [tty0] enabled
[    0.004000] Dentry cache hash table entries: 262144 (order: 9, 2097152 bytes)
[    0.004000] Inode-cache hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.004000] allocated 19660800 bytes of page_cgroup
[    0.004000] please try cgroup_disable=memory option if you don't want
[    0.004000] Scanning for low memory corruption every 60 seconds
[    0.004000] Checking aperture...
[    0.004000] No AGP bridge found
[    0.004000] Node 0: aperture @ 49e4000000 size 32 MB
[    0.004000] Aperture beyond 4GB. Ignoring.
[    0.004000] Memory: 1894708k/1964928k available (4743k kernel code, 452k absent, 69084k reserved, 2525k data, 532k init)
[    0.004000] SLUB: Genslabs=12, HWalign=64, Order=0-3, MinObjects=0, CPUs=4, Nodes=1
[    0.004000] hpet clockevent registered
[    0.004000] HPET: 4 timers in total, 0 timers will be used for per-cpu timer
[    0.004010] Calibrating delay loop (skipped), value calculated using timer frequency.. 3799.83 BogoMIPS (lpj=7599668)
[    0.004032] Security Framework initialized
[    0.004039] SELinux:  Disabled at boot.
[    0.004057] AppArmor: AppArmor initialized
[    0.004066] Mount-cache hash table entries: 256
[    0.004223] Initializing cgroup subsys ns
[    0.004227] Initializing cgroup subsys cpuacct
[    0.004229] Initializing cgroup subsys memory
[    0.004234] Initializing cgroup subsys freezer
[    0.004246] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[    0.004248] CPU: L2 Cache: 512K (64 bytes/line)
[    0.004250] tseg: 0077f00000
[    0.004252] CPU: Physical Processor ID: 0
[    0.004253] CPU: Processor Core ID: 0
[    0.004256] using C1E aware idle routine
[    0.005966] ACPI: Core revision 20080926
[    0.007598] ACPI: Checking initramfs for custom DSDT
[    0.320066] Setting APIC routing to flat
[    0.320643] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.361714] CPU0: AMD Athlon(tm) X2 Dual Core Processor BE-2300 stepping 02
[    0.364001] Booting processor 1 APIC 0x1 ip 0x6000
[    0.004000] Initializing CPU#1
[    0.004000] Calibrating delay using timer specific routine.. 3799.85 BogoMIPS (lpj=7599713)
[    0.004000] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[    0.004000] CPU: L2 Cache: 512K (64 bytes/line)
[    0.004000] CPU: Physical Processor ID: 0
[    0.004000] CPU: Processor Core ID: 1
[    0.448180] CPU1: AMD Athlon(tm) X2 Dual Core Processor BE-2300 stepping 02
[    0.448197] Brought up 2 CPUs
[    0.448199] Total of 2 processors activated (7599.69 BogoMIPS).
[    0.448304] CPU0 attaching sched-domain:
[    0.448306]  domain 0: span 0-1 level CPU
[    0.448308]   groups: 0 1
[    0.448314] CPU1 attaching sched-domain:
[    0.448315]  domain 0: span 0-1 level CPU
[    0.448317]   groups: 1 0
[    0.448382] net_namespace: 1400 bytes
[    0.448382] Booting paravirtualized kernel on bare hardware
[    0.448382] Time:  4:00:14  Date: 07/10/09
[    0.448382] regulator: core version 0.5
[    0.448382] NET: Registered protocol family 16
[    0.448382] node 0 link 0: io port [b000, ffff]
[    0.448382] TOM: 0000000080000000 aka 2048M
[    0.448382] node 0 link 0: mmio [a0000, bffff]
[    0.448382] node 0 link 0: mmio [80000000, dfffffff]
[    0.448382] node 0 link 0: mmio [f0000000, fe02ffff]
[    0.448382] node 0 link 0: mmio [e0000000, e03fffff]
[    0.448382] bus: [00,03] on node 0 link 0
[    0.448382] bus: 00 index 0 io port: [0, ffff]
[    0.448382] bus: 00 index 1 mmio: [a0000, bffff]
[    0.448382] bus: 00 index 2 mmio: [80000000, efffffff]
[    0.448382] bus: 00 index 3 mmio: [f0000000, fcffffffff]
[    0.448382] ACPI: bus type pci registered
[    0.448382] PCI: MCFG configuration 0: base e0000000 segment 0 buses 0 - 255
[    0.448382] PCI: MCFG area at e0000000 reserved in E820
[    0.463726] PCI: Using MMCONFIG at e0000000 - efffffff
[    0.463729] PCI: Using configuration type 1 for base access
[    0.464499] ACPI: EC: Look up EC in DSDT
[    0.472395] ACPI: Interpreter enabled
[    0.472399] ACPI: (supports S0 S1 S3 S4 S5)
[    0.472420] ACPI: Using IOAPIC for interrupt routing
[    0.477501] ACPI: No dock devices found.
[    0.477511] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.477611] pci 0000:00:07.0: PME# supported from D0 D3hot D3cold
[    0.477615] pci 0000:00:07.0: PME# disabled
[    0.477668] pci 0000:00:12.0: reg 10 io port: [0xfc00-0xfc07]
[    0.477676] pci 0000:00:12.0: reg 14 io port: [0xf800-0xf803]
[    0.477683] pci 0000:00:12.0: reg 18 io port: [0xf400-0xf407]
[    0.477691] pci 0000:00:12.0: reg 1c io port: [0xf000-0xf003]
[    0.477698] pci 0000:00:12.0: reg 20 io port: [0xec00-0xec0f]
[    0.477706] pci 0000:00:12.0: reg 24 32bit mmio: [0xfe02f000-0xfe02f3ff]
[    0.477726] pci 0000:00:12.0: set SATA to AHCI mode
[    0.477758] pci 0000:00:13.0: reg 10 32bit mmio: [0xfe02e000-0xfe02efff]
[    0.477816] pci 0000:00:13.1: reg 10 32bit mmio: [0xfe02d000-0xfe02dfff]
[    0.477874] pci 0000:00:13.2: reg 10 32bit mmio: [0xfe02c000-0xfe02cfff]
[    0.477935] pci 0000:00:13.3: reg 10 32bit mmio: [0xfe02b000-0xfe02bfff]
[    0.477993] pci 0000:00:13.4: reg 10 32bit mmio: [0xfe02a000-0xfe02afff]
[    0.478073] pci 0000:00:13.5: reg 10 32bit mmio: [0xfe029000-0xfe0290ff]
[    0.478115] pci 0000:00:13.5: supports D1 D2
[    0.478117] pci 0000:00:13.5: PME# supported from D0 D1 D2 D3hot
[    0.478122] pci 0000:00:13.5: PME# disabled
[    0.478438] pci 0000:00:14.0: reg 10 io port: [0xb00-0xb0f]
[    0.479035] pci 0000:00:14.1: reg 10 io port: [0x00-0x07]
[    0.479043] pci 0000:00:14.1: reg 14 io port: [0x00-0x03]
[    0.479050] pci 0000:00:14.1: reg 18 io port: [0x00-0x07]
[    0.479057] pci 0000:00:14.1: reg 1c io port: [0x00-0x03]
[    0.479064] pci 0000:00:14.1: reg 20 io port: [0xe400-0xe40f]
[    0.479120] pci 0000:00:14.2: reg 10 64bit mmio: [0xfe020000-0xfe023fff]
[    0.479158] pci 0000:00:14.2: PME# supported from D0 D3hot D3cold
[    0.479162] pci 0000:00:14.2: PME# disabled
[    0.479372] pci 0000:01:05.0: reg 10 64bit mmio: [0xf0000000-0xf7ffffff]
[    0.479379] pci 0000:01:05.0: reg 18 64bit mmio: [0xfdbf0000-0xfdbfffff]
[    0.479384] pci 0000:01:05.0: reg 20 io port: [0xcc00-0xccff]
[    0.479388] pci 0000:01:05.0: reg 24 32bit mmio: [0xfda00000-0xfdafffff]
[    0.479395] pci 0000:01:05.0: supports D1 D2
[    0.479415] pci 0000:00:01.0: bridge io port: [0xc000-0xcfff]
[    0.479418] pci 0000:00:01.0: bridge 32bit mmio: [0xfda00000-0xfdbfffff]
[    0.479422] pci 0000:00:01.0: bridge 64bit mmio pref: [0xf0000000-0xf7ffffff]
[    0.479470] pci 0000:02:00.0: reg 10 io port: [0xdc00-0xdcff]
[    0.479489] pci 0000:02:00.0: reg 18 64bit mmio: [0xfdfff000-0xfdffffff]
[    0.479508] pci 0000:02:00.0: reg 30 32bit mmio: [0x000000-0x01ffff]
[    0.479519] pci 0000:02:00.0: supports D1 D2
[    0.479521] pci 0000:02:00.0: PME# supported from D1 D2 D3hot D3cold
[    0.479526] pci 0000:02:00.0: PME# disabled
[    0.479583] pci 0000:00:07.0: bridge io port: [0xd000-0xdfff]
[    0.479586] pci 0000:00:07.0: bridge 32bit mmio: [0xfdf00000-0xfdffffff]
[    0.479590] pci 0000:00:07.0: bridge 64bit mmio pref: [0xfdc00000-0xfdcfffff]
[    0.479653] pci 0000:00:14.4: transparent bridge
[    0.479657] pci 0000:00:14.4: bridge io port: [0xb000-0xbfff]
[    0.479662] pci 0000:00:14.4: bridge 32bit mmio: [0xfde00000-0xfdefffff]
[    0.479667] pci 0000:00:14.4: bridge 32bit mmio pref: [0xfdd00000-0xfddfffff]
[    0.479680] bus 00 -> node 0
[    0.479686] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.480041] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P2P_._PRT]
[    0.480216] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCE7._PRT]
[    0.480317] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.AGP_._PRT]
[    0.507891] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 10 11) *0, disabled.
[    0.508020] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 10 11) *0, disabled.
[    0.508136] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 10 11) *0, disabled.
[    0.508256] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 10 11) *0, disabled.
[    0.508372] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 10 11) *0, disabled.
[    0.508488] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 10 11) *0, disabled.
[    0.508603] ACPI: PCI Interrupt Link [LNK0] (IRQs 3 4 5 6 7 10 *11)
[    0.508718] ACPI: PCI Interrupt Link [LNK1] (IRQs 3 4 5 6 7 10 11) *0, disabled.
[    0.508853] ACPI: WMI: Mapper loaded
[    0.508932] SCSI subsystem initialized
[    0.508932] libata version 3.00 loaded.
[    0.508932] usbcore: registered new interface driver usbfs
[    0.508932] usbcore: registered new interface driver hub
[    0.508932] usbcore: registered new device driver usb
[    0.508932] PCI: Using ACPI for IRQ routing
[    0.520011] Bluetooth: Core ver 2.13
[    0.520026] NET: Registered protocol family 31
[    0.520026] Bluetooth: HCI device and connection manager initialized
[    0.520026] Bluetooth: HCI socket layer initialized
[    0.520026] NET: Registered protocol family 8
[    0.520027] NET: Registered protocol family 20
[    0.520037] NetLabel: Initializing
[    0.520039] NetLabel:  domain hash size = 128
[    0.520040] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.520054] NetLabel:  unlabeled traffic allowed by default
[    0.520284] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0, 0
[    0.520288] hpet0: 4 comparators, 32-bit 14.318180 MHz counter
[    0.524073] AppArmor: AppArmor Filesystem Enabled
[    0.528015] Switched to high resolution mode on CPU 0
[    0.528194] Switched to high resolution mode on CPU 1
[    0.536016] pnp: PnP ACPI init
[    0.536028] ACPI: bus type pnp registered
[    0.539373] pnp: PnP ACPI: found 14 devices
[    0.539375] ACPI: ACPI bus type pnp unregistered
[    0.539385] system 00:01: ioport range 0x4100-0x411f has been reserved
[    0.539387] system 00:01: ioport range 0x228-0x22f has been reserved
[    0.539390] system 00:01: ioport range 0x40b-0x40b has been reserved
[    0.539393] system 00:01: ioport range 0x4d6-0x4d6 has been reserved
[    0.539395] system 00:01: ioport range 0xc00-0xc01 has been reserved
[    0.539398] system 00:01: ioport range 0xc14-0xc14 has been reserved
[    0.539400] system 00:01: ioport range 0xc50-0xc52 has been reserved
[    0.539402] system 00:01: ioport range 0xc6c-0xc6d has been reserved
[    0.539405] system 00:01: ioport range 0xc6f-0xc6f has been reserved
[    0.539407] system 00:01: ioport range 0xcd0-0xcd1 has been reserved
[    0.539410] system 00:01: ioport range 0xcd2-0xcd3 has been reserved
[    0.539412] system 00:01: ioport range 0xcd4-0xcdf has been reserved
[    0.539414] system 00:01: ioport range 0x4000-0x40fe has been reserved
[    0.539417] system 00:01: ioport range 0x4210-0x4217 has been reserved
[    0.539419] system 00:01: ioport range 0xb00-0xb0f has been reserved
[    0.539422] system 00:01: ioport range 0xb10-0xb1f has been reserved
[    0.539428] system 00:07: ioport range 0x4d0-0x4d1 has been reserved
[    0.539431] system 00:07: ioport range 0x220-0x225 has been reserved
[    0.539437] system 00:0c: iomem range 0xe0000000-0xefffffff has been reserved
[    0.539442] system 00:0d: iomem range 0xcd600-0xcffff has been reserved
[    0.539445] system 00:0d: iomem range 0xf0000-0xf7fff could not be reserved
[    0.539448] system 00:0d: iomem range 0xf8000-0xfbfff could not be reserved
[    0.539450] system 00:0d: iomem range 0xfc000-0xfffff could not be reserved
[    0.539453] system 00:0d: iomem range 0x77ef0000-0x77feffff could not be reserved
[    0.539456] system 00:0d: iomem range 0xfed00000-0xfed000ff has been reserved
[    0.539459] system 00:0d: iomem range 0x77ee0000-0x77efffff could not be reserved
[    0.539461] system 00:0d: iomem range 0xffff0000-0xffffffff has been reserved
[    0.539464] system 00:0d: iomem range 0x0-0x9ffff could not be reserved
[    0.539467] system 00:0d: iomem range 0x100000-0x77edffff could not be reserved
[    0.539470] system 00:0d: iomem range 0x77ff0000-0x7ffeffff has been reserved
[    0.539472] system 00:0d: iomem range 0xfec00000-0xfec00fff has been reserved
[    0.539475] system 00:0d: iomem range 0xfee00000-0xfee00fff has been reserved
[    0.539478] system 00:0d: iomem range 0xfff80000-0xfffeffff has been reserved
[    0.544165] pci 0000:00:01.0: PCI bridge, secondary bus 0000:01
[    0.544168] pci 0000:00:01.0:   IO window: 0xc000-0xcfff
[    0.544172] pci 0000:00:01.0:   MEM window: 0xfda00000-0xfdbfffff
[    0.544175] pci 0000:00:01.0:   PREFETCH window: 0x000000f0000000-0x000000f7ffffff
[    0.544182] pci 0000:00:07.0: PCI bridge, secondary bus 0000:02
[    0.544184] pci 0000:00:07.0:   IO window: 0xd000-0xdfff
[    0.544188] pci 0000:00:07.0:   MEM window: 0xfdf00000-0xfdffffff
[    0.544191] pci 0000:00:07.0:   PREFETCH window: 0x000000fdc00000-0x000000fdcfffff
[    0.544195] pci 0000:00:14.4: PCI bridge, secondary bus 0000:03
[    0.544198] pci 0000:00:14.4:   IO window: 0xb000-0xbfff
[    0.544204] pci 0000:00:14.4:   MEM window: 0xfde00000-0xfdefffff
[    0.544208] pci 0000:00:14.4:   PREFETCH window: 0x000000fdd00000-0x000000fddfffff
[    0.544224] pci 0000:00:07.0: setting latency timer to 64
[    0.544232] bus: 00 index 0 io port: [0x00-0xffff]
[    0.544234] bus: 00 index 1 mmio: [0x000000-0xffffffffffffffff]
[    0.544236] bus: 01 index 0 io port: [0xc000-0xcfff]
[    0.544238] bus: 01 index 1 mmio: [0xfda00000-0xfdbfffff]
[    0.544240] bus: 01 index 2 mmio: [0xf0000000-0xf7ffffff]
[    0.544242] bus: 01 index 3 mmio: [0x0-0x0]
[    0.544244] bus: 02 index 0 io port: [0xd000-0xdfff]
[    0.544245] bus: 02 index 1 mmio: [0xfdf00000-0xfdffffff]
[    0.544247] bus: 02 index 2 mmio: [0xfdc00000-0xfdcfffff]
[    0.544249] bus: 02 index 3 mmio: [0x0-0x0]
[    0.544251] bus: 03 index 0 io port: [0xb000-0xbfff]
[    0.544253] bus: 03 index 1 mmio: [0xfde00000-0xfdefffff]
[    0.544255] bus: 03 index 2 mmio: [0xfdd00000-0xfddfffff]
[    0.544257] bus: 03 index 3 io port: [0x00-0xffff]
[    0.544259] bus: 03 index 4 mmio: [0x000000-0xffffffffffffffff]
[    0.544270] NET: Registered protocol family 2
[    0.580072] IP route cache hash table entries: 65536 (order: 7, 524288 bytes)
[    0.580568] TCP established hash table entries: 262144 (order: 10, 4194304 bytes)
[    0.583104] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[    0.583740] TCP: Hash tables configured (established 262144 bind 65536)
[    0.583743] TCP reno registered
[    0.592136] NET: Registered protocol family 1
[    0.592264] checking if image is initramfs... it is
[    1.228050] Freeing initrd memory: 8015k freed
[    1.233195] audit: initializing netlink socket (disabled)
[    1.233216] type=2000 audit(1247198414.232:1): initialized
[    1.241691] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    1.242962] VFS: Disk quotas dquot_6.5.1
[    1.243016] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[    1.243631] fuse init (API version 7.10)
[    1.243713] msgmni has been set to 3717
[    1.243916] alg: No test for stdrng (krng)
[    1.243930] io scheduler noop registered
[    1.243932] io scheduler anticipatory registered
[    1.243934] io scheduler deadline registered
[    1.243981] io scheduler cfq registered (default)
[    1.504543] pci 0000:01:05.0: Boot video device
[    1.507365] pcieport-driver 0000:00:07.0: setting latency timer to 64
[    1.507384] pcieport-driver 0000:00:07.0: found MSI capability
[    1.507402] pcieport-driver 0000:00:07.0: irq 2303 for MSI/MSI-X
[    1.507409] pci_express 0000:00:07.0:pcie00: allocate port service
[    1.507423] pci_express 0000:00:07.0:pcie03: allocate port service
[    1.507473] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    1.507485] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    1.507615] input: Power Button (FF) as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input0
[    1.507618] ACPI: Power Button (FF) [PWRF]
[    1.507658] input: Power Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input1
[    1.507661] ACPI: Power Button (CM) [PWRB]
[    1.507706] fan PNP0C0B:00: registered as cooling_device0
[    1.507713] ACPI: Fan [FAN] (on)
[    1.507941] processor ACPI_CPU:00: registered as cooling_device1
[    1.507975] processor ACPI_CPU:01: registered as cooling_device2
[    1.510385] ACPI Warning (nspredef-0858): \_TZ_.THRM._PSL: Return Package type mismatch at index 0 - found [NULL Object Descriptor], expected Reference [20080926]
[    1.510393] ACPI: Expecting a [Reference] package element, found type 0
[    1.510604] thermal LNXTHERM:01: registered as thermal_zone0
[    1.510937] ACPI: Thermal Zone [THRM] (40 C)
[    1.536733] Linux agpgart interface v0.103
[    1.536742] Serial: 8250/16550 driver4 ports, IRQ sharing enabled
[    1.536858] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    1.537172] 00:09: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    1.537926] brd: module loaded
[    1.538241] loop: module loaded
[    1.538317] Fixed MDIO Bus: probed
[    1.538323] PPP generic driver version 2.4.2
[    1.538377] input: Macintosh mouse button emulation as /devices/virtual/input/input2
[    1.538409] Driver 'sd' needs updating - please use bus_type methods
[    1.538418] Driver 'sr' needs updating - please use bus_type methods
[    1.538455] ahci 0000:00:12.0: version 3.0
[    1.538480] ahci 0000:00:12.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[    1.538516] ahci 0000:00:12.0: controller can't do 64bit DMA, forcing 32bit
[    1.538606] ahci 0000:00:12.0: AHCI 0001.0100 32 slots 4 ports 3 Gbps 0xf impl SATA mode
[    1.538609] ahci 0000:00:12.0: flags: ncq sntf ilck pm led clo pmp pio slum part 
[    1.539060] scsi0 : ahci
[    1.539209] scsi1 : ahci
[    1.539285] scsi2 : ahci
[    1.539356] scsi3 : ahci
[    1.539460] ata1: SATA max UDMA/133 abar m1024@0xfe02f000 port 0xfe02f100 irq 22
[    1.539463] ata2: SATA max UDMA/133 abar m1024@0xfe02f000 port 0xfe02f180 irq 22
[    1.539467] ata3: SATA max UDMA/133 abar m1024@0xfe02f000 port 0xfe02f200 irq 22
[    1.539470] ata4: SATA max UDMA/133 abar m1024@0xfe02f000 port 0xfe02f280 irq 22
[    2.020018] ata1: softreset failed (device not ready)
[    2.020058] ata1: failed due to HW bug, retry pmp=0
[    2.184028] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    2.184649] ata1.00: ATA-7: Maxtor 6Y060M0, YAR511W0, max UDMA/133
[    2.184651] ata1.00: 120103200 sectors, multi 0: LBA 
[    2.184668] ata1.00: SB600 AHCI: limiting to 255 sectors per cmd
[    2.185423] ata1.00: SB600 AHCI: limiting to 255 sectors per cmd
[    2.185426] ata1.00: configured for UDMA/133
[    2.684017] ata2: softreset failed (device not ready)
[    2.684055] ata2: failed due to HW bug, retry pmp=0
[    2.848028] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    2.848642] ata2.00: ATA-7: Maxtor 6Y060M0, YAR511W0, max UDMA/133
[    2.848644] ata2.00: 120103200 sectors, multi 0: LBA 
[    2.848660] ata2.00: SB600 AHCI: limiting to 255 sectors per cmd
[    2.849390] ata2.00: SB600 AHCI: limiting to 255 sectors per cmd
[    2.849392] ata2.00: configured for UDMA/133
[    3.348017] ata3: softreset failed (device not ready)
[    3.348052] ata3: failed due to HW bug, retry pmp=0
[    3.512030] ata3: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    3.518378] ata3.00: ATA-7: SAMSUNG HD103SI, 1AG01113, max UDMA7
[    3.518380] ata3.00: 1953525168 sectors, multi 1: LBA48 NCQ (depth 31/32)
[    3.518397] ata3.00: SB600 AHCI: limiting to 255 sectors per cmd
[    3.524828] ata3.00: SB600 AHCI: limiting to 255 sectors per cmd
[    3.524830] ata3.00: configured for UDMA/133
[    4.024016] ata4: softreset failed (device not ready)
[    4.024050] ata4: failed due to HW bug, retry pmp=0
[    4.188027] ata4: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    4.194376] ata4.00: ATA-7: SAMSUNG HD103SI, 1AG01113, max UDMA7
[    4.194378] ata4.00: 1953525168 sectors, multi 1: LBA48 NCQ (depth 31/32)
[    4.194395] ata4.00: SB600 AHCI: limiting to 255 sectors per cmd
[    4.200828] ata4.00: SB600 AHCI: limiting to 255 sectors per cmd
[    4.200830] ata4.00: configured for UDMA/133
[    4.216045] isa bounce pool size: 16 pages
[    4.216134] scsi 0:0:0:0: Direct-Access     ATA      Maxtor 6Y060M0   YAR5 PQ: 0 ANSI: 5
[    4.216231] sd 0:0:0:0: [sda] 120103200 512-byte hardware sectors: (61.4 GB/57.2 GiB)
[    4.216248] sd 0:0:0:0: [sda] Write Protect is off
[    4.216250] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    4.216274] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    4.216353] sd 0:0:0:0: [sda] 120103200 512-byte hardware sectors: (61.4 GB/57.2 GiB)
[    4.216367] sd 0:0:0:0: [sda] Write Protect is off
[    4.216369] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    4.216392] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    4.216396]  sda: sda1 sda2 < sda5 >
[    4.251401] sd 0:0:0:0: [sda] Attached SCSI disk
[    4.251465] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    4.251523] scsi 1:0:0:0: Direct-Access     ATA      Maxtor 6Y060M0   YAR5 PQ: 0 ANSI: 5
[    4.251606] sd 1:0:0:0: [sdb] 120103200 512-byte hardware sectors: (61.4 GB/57.2 GiB)
[    4.251620] sd 1:0:0:0: [sdb] Write Protect is off
[    4.251622] sd 1:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[    4.251645] sd 1:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    4.251691] sd 1:0:0:0: [sdb] 120103200 512-byte hardware sectors: (61.4 GB/57.2 GiB)
[    4.251705] sd 1:0:0:0: [sdb] Write Protect is off
[    4.251707] sd 1:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[    4.251730] sd 1:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    4.251734]  sdb: sdb1
[    4.260500] sd 1:0:0:0: [sdb] Attached SCSI disk
[    4.260544] sd 1:0:0:0: Attached scsi generic sg1 type 0
[    4.260597] scsi 2:0:0:0: Direct-Access     ATA      SAMSUNG HD103SI  1AG0 PQ: 0 ANSI: 5
[    4.260675] sd 2:0:0:0: [sdc] 1953525168 512-byte hardware sectors: (1.00 TB/931 GiB)
[    4.260688] sd 2:0:0:0: [sdc] Write Protect is off
[    4.260690] sd 2:0:0:0: [sdc] Mode Sense: 00 3a 00 00
[    4.260713] sd 2:0:0:0: [sdc] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    4.260762] sd 2:0:0:0: [sdc] 1953525168 512-byte hardware sectors: (1.00 TB/931 GiB)
[    4.260775] sd 2:0:0:0: [sdc] Write Protect is off
[    4.260778] sd 2:0:0:0: [sdc] Mode Sense: 00 3a 00 00
[    4.260800] sd 2:0:0:0: [sdc] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    4.260803]  sdc: unknown partition table
[    4.272318] sd 2:0:0:0: [sdc] Attached SCSI disk
[    4.272354] sd 2:0:0:0: Attached scsi generic sg2 type 0
[    4.272410] scsi 3:0:0:0: Direct-Access     ATA      SAMSUNG HD103SI  1AG0 PQ: 0 ANSI: 5
[    4.272487] sd 3:0:0:0: [sdd] 1953525168 512-byte hardware sectors: (1.00 TB/931 GiB)
[    4.272509] sd 3:0:0:0: [sdd] Write Protect is off
[    4.272512] sd 3:0:0:0: [sdd] Mode Sense: 00 3a 00 00
[    4.272536] sd 3:0:0:0: [sdd] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    4.272582] sd 3:0:0:0: [sdd] 1953525168 512-byte hardware sectors: (1.00 TB/931 GiB)
[    4.272595] sd 3:0:0:0: [sdd] Write Protect is off
[    4.272597] sd 3:0:0:0: [sdd] Mode Sense: 00 3a 00 00
[    4.272620] sd 3:0:0:0: [sdd] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    4.272623]  sdd: unknown partition table
[    4.278809] sd 3:0:0:0: [sdd] Attached SCSI disk
[    4.278842] sd 3:0:0:0: Attached scsi generic sg3 type 0
[    4.279098] pata_atiixp 0000:00:14.1: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    4.279240] scsi4 : pata_atiixp
[    4.279316] scsi5 : pata_atiixp
[    4.279885] ata5: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0xe400 irq 14
[    4.279888] ata6: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xe408 irq 15
[    4.449362] ata5.00: ATA-5: WDC WD600BB-00CAA1, 17.07W17, max UDMA/100
[    4.449364] ata5.00: 117231408 sectors, multi 1: LBA 
[    4.449391] ata5.01: ATAPI: HP      DVD Writer 840b, HJ86, max UDMA/33
[    4.465296] ata5.00: configured for UDMA/100
[    4.480524] ata5.01: configured for UDMA/33
[    4.636145] scsi 4:0:0:0: Direct-Access     ATA      WDC WD600BB-00CA 17.0 PQ: 0 ANSI: 5
[    4.636227] sd 4:0:0:0: [sde] 117231408 512-byte hardware sectors: (60.0 GB/55.8 GiB)
[    4.636243] sd 4:0:0:0: [sde] Write Protect is off
[    4.636245] sd 4:0:0:0: [sde] Mode Sense: 00 3a 00 00
[    4.636269] sd 4:0:0:0: [sde] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    4.636329] sd 4:0:0:0: [sde] 117231408 512-byte hardware sectors: (60.0 GB/55.8 GiB)
[    4.636343] sd 4:0:0:0: [sde] Write Protect is off
[    4.636345] sd 4:0:0:0: [sde] Mode Sense: 00 3a 00 00
[    4.636368] sd 4:0:0:0: [sde] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    4.636372]  sde: sde1
[    4.642733] sd 4:0:0:0: [sde] Attached SCSI disk
[    4.642779] sd 4:0:0:0: Attached scsi generic sg4 type 0
[    4.644481] scsi 4:0:1:0: CD-ROM            HP       DVD Writer 840b  HJ86 PQ: 0 ANSI: 5
[    4.649708] sr0: scsi3-mmc drive: 40x/40x writer dvd-ram cd/rw xa/form2 cdda tray
[    4.649711] Uniform CD-ROM driver Revision: 3.20
[    4.649797] sr 4:0:1:0: Attached scsi CD-ROM sr0
[    4.649832] sr 4:0:1:0: Attached scsi generic sg5 type 5
[    4.650209] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    4.650238] ehci_hcd 0000:00:13.5: PCI INT D -> GSI 19 (level, low) -> IRQ 19
[    4.650258] ehci_hcd 0000:00:13.5: EHCI Host Controller
[    4.650314] ehci_hcd 0000:00:13.5: new USB bus registered, assigned bus number 1
[    4.650345] ehci_hcd 0000:00:13.5: applying AMD SB600/SB700 USB freeze workaround
[    4.650364] ehci_hcd 0000:00:13.5: debug port 1
[    4.650393] ehci_hcd 0000:00:13.5: irq 19, io mem 0xfe029000
[    4.660019] ehci_hcd 0000:00:13.5: USB 2.0 started, EHCI 1.00
[    4.660096] usb usb1: configuration #1 chosen from 1 choice
[    4.660124] hub 1-0:1.0: USB hub found
[    4.660131] hub 1-0:1.0: 10 ports detected
[    4.660254] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    4.660268] ohci_hcd 0000:00:13.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    4.660279] ohci_hcd 0000:00:13.0: OHCI Host Controller
[    4.660321] ohci_hcd 0000:00:13.0: new USB bus registered, assigned bus number 2
[    4.660349] ohci_hcd 0000:00:13.0: irq 16, io mem 0xfe02e000
[    4.720046] usb usb2: configuration #1 chosen from 1 choice
[    4.720067] hub 2-0:1.0: USB hub found
[    4.720077] hub 2-0:1.0: 2 ports detected
[    4.720160] ohci_hcd 0000:00:13.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    4.720173] ohci_hcd 0000:00:13.1: OHCI Host Controller
[    4.720210] ohci_hcd 0000:00:13.1: new USB bus registered, assigned bus number 3
[    4.720236] ohci_hcd 0000:00:13.1: irq 17, io mem 0xfe02d000
[    4.776043] usb usb3: configuration #1 chosen from 1 choice
[    4.776064] hub 3-0:1.0: USB hub found
[    4.776073] hub 3-0:1.0: 2 ports detected
[    4.776160] ohci_hcd 0000:00:13.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    4.776170] ohci_hcd 0000:00:13.2: OHCI Host Controller
[    4.776223] ohci_hcd 0000:00:13.2: new USB bus registered, assigned bus number 4
[    4.776250] ohci_hcd 0000:00:13.2: irq 18, io mem 0xfe02c000
[    4.832042] usb usb4: configuration #1 chosen from 1 choice
[    4.832072] hub 4-0:1.0: USB hub found
[    4.832081] hub 4-0:1.0: 2 ports detected
[    4.832157] ohci_hcd 0000:00:13.3: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    4.832167] ohci_hcd 0000:00:13.3: OHCI Host Controller
[    4.832208] ohci_hcd 0000:00:13.3: new USB bus registered, assigned bus number 5
[    4.832221] ohci_hcd 0000:00:13.3: irq 17, io mem 0xfe02b000
[    4.888047] usb usb5: configuration #1 chosen from 1 choice
[    4.888069] hub 5-0:1.0: USB hub found
[    4.888078] hub 5-0:1.0: 2 ports detected
[    4.888156] ohci_hcd 0000:00:13.4: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    4.888166] ohci_hcd 0000:00:13.4: OHCI Host Controller
[    4.888203] ohci_hcd 0000:00:13.4: new USB bus registered, assigned bus number 6
[    4.888216] ohci_hcd 0000:00:13.4: irq 18, io mem 0xfe02a000
[    4.944047] usb usb6: configuration #1 chosen from 1 choice
[    4.944069] hub 6-0:1.0: USB hub found
[    4.944078] hub 6-0:1.0: 2 ports detected
[    4.944163] uhci_hcd: USB Universal Host Controller Interface driver
[    4.944242] PNP: PS/2 Controller [PNP0303:PS2K] at 0x60,0x64 irq 1
[    4.944244] PNP: PS/2 appears to have AUX port disabled, if this is incorrect please boot with i8042.nopnp
[    4.944321] serio: i8042 KBD port at 0x60,0x64 irq 1
[    4.952543] mice: PS/2 mouse device common for all mice
[    4.988563] rtc_cmos 00:04: RTC can wake from S4
[    4.988599] rtc_cmos 00:04: rtc core: registered rtc_cmos as rtc0
[    4.988634] rtc0: alarms up to one month, 242 bytes nvram, hpet irqs
[    4.988699] device-mapper: uevent: version 1.0.3
[    4.996130] device-mapper: ioctl: 4.14.0-ioctl (2008-04-23) initialised: [EMAIL="dm-devel@redhat.com"]dm-devel@redhat.com[/EMAIL]
[    4.996203] device-mapper: multipath: version 1.0.5 loaded
[    4.996206] device-mapper: multipath round-robin: version 1.0.0 loaded
[    4.996299] cpuidle: using governor ladder
[    4.996301] cpuidle: using governor menu
[    4.996741] TCP cubic registered
[    4.996820] NET: Registered protocol family 10
[    4.997222] lo: Disabled Privacy Extensions
[    4.997495] NET: Registered protocol family 17
[    4.997521] Bluetooth: L2CAP ver 2.11
[    4.997522] Bluetooth: L2CAP socket layer initialized
[    4.997525] Bluetooth: SCO (Voice Link) ver 0.6
[    4.997526] Bluetooth: SCO socket layer initialized
[    4.997556] Bluetooth: RFCOMM socket layer initialized
[    4.997563] Bluetooth: RFCOMM TTY layer initialized
[    4.997565] Bluetooth: RFCOMM ver 1.10
[    4.998653] powernow-k8: Found 1 AMD Athlon(tm) X2 Dual Core Processor BE-2300 processors (2 cpu cores) (version 2.20.00)
[    4.998718] powernow-k8:    0 : fid 0xb (1900 MHz), vid 0xe
[    4.998721] powernow-k8:    1 : fid 0xa (1800 MHz), vid 0xf
[    4.998723] powernow-k8:    2 : fid 0x2 (1000 MHz), vid 0x16
[    4.998869] registered taskstats version 1
[    4.999023]   Magic number: 1:140:9
[    4.999030] hub 4-0:1.0: hash matches
[    4.999123] rtc_cmos 00:04: setting system clock to 2009-07-10 04:00:18 UTC (1247198418)
[    4.999126] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    4.999128] EDD information not available.
[    4.999172] Freeing unused kernel memory: 532k freed
[    4.999456] Write protecting the kernel read-only data: 6684k
[    5.010347] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input3
[    5.108567] usb 3-1: new low speed USB device using ohci_hcd and address 2
[    5.172292] md: linear personality registered for level -1
[    5.175017] md: multipath personality registered for level -4
[    5.177323] md: raid0 personality registered for level 0
[    5.180810] md: raid1 personality registered for level 1
[    5.182917] xor: automatically using best checksumming function: generic_sse
[    5.200504]    generic_sse:  5680.000 MB/sec
[    5.200506] xor: using function: generic_sse (5680.000 MB/sec)
[    5.201751] async_tx: api initialized (async)
[    5.272538] raid6: int64x1   1577 MB/s
[    5.280122] usb 3-1: configuration #1 chosen from 1 choice
[    5.340527] raid6: int64x2   2158 MB/s
[    5.408524] raid6: int64x4   1733 MB/s
[    5.476527] raid6: int64x8   1612 MB/s
[    5.544508] raid6: sse2x1    2639 MB/s
[    5.612517] raid6: sse2x2    3516 MB/s
[    5.680518] raid6: sse2x4    3658 MB/s
[    5.680520] raid6: using algorithm sse2x4 (3658 MB/s)
[    5.680522] md: raid6 personality registered for level 6
[    5.680524] md: raid5 personality registered for level 5
[    5.680526] md: raid4 personality registered for level 4
[    5.688214] md: raid10 personality registered for level 10
[    5.732874] Floppy drive(s): fd0 is 1.44M
[    5.752344] FDC 0 is a post-1991 82077
[    5.758160] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[    5.758182] r8169 0000:02:00.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[    5.758202] r8169 0000:02:00.0: setting latency timer to 64
[    5.758312] r8169 0000:02:00.0: irq 2302 for MSI/MSI-X
[    5.758898] eth0: RTL8168b/8111b at 0xffffc2001010e000, 00:1e:8c:a7:91:ca, XID 38000000 IRQ 2302
[    5.801530] usbcore: registered new interface driver hiddev
[    5.805391] input: Logitech USB Optical Mouse as /devices/pci0000:00/0000:00:13.1/usb3/3-1/3-1:1.0/input/input4
[    5.828788] generic-usb 0003:046D:C018.0001: input,hidraw0: USB HID v1.11 Mouse [Logitech USB Optical Mouse] on usb-0000:00:13.1-1/input0
[    5.828813] usbcore: registered new interface driver usbhid
[    5.828816] usbhid: v2.6:USB HID core driver
[    6.063253] PM: Starting manual resume from disk
[    6.063256] PM: Resume from partition 8:5
[    6.063258] PM: Checking hibernation image.
[    6.063469] PM: Resume from disk failed.
[    6.102926] kjournald starting.  Commit interval 5 seconds
[    6.102949] EXT3-fs: mounted filesystem with ordered data mode.
[   11.667813] udev: starting version 141
[   11.961353] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   12.245397] input: PC Speaker as /devices/platform/pcspkr/input/input5
[   12.418902] piix4_smbus 0000:00:14.0: SMBus Host Controller at 0xb00, revision 0
[   12.447023] parport_pc 00:0a: reported by Plug and Play ACPI
[   12.447056] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE,EPP]
[   12.613230] ppdev: user-space parallel port driver
[   12.656953] md: bind<sdc>
[   12.882533] HDA Intel 0000:00:14.2: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   13.072561] lp0: using parport0 (interrupt-driven).
[   13.211927] Adding 2498068k swap on /dev/sda5.  Priority:-1 extents:1 across:2498068k
[   13.762744] EXT3 FS on sda1, internal journal
[   15.569798] kjournald starting.  Commit interval 5 seconds
[   15.570090] EXT3 FS on sdb1, internal journal
[   15.570095] EXT3-fs: mounted filesystem with ordered data mode.
[   15.622384] kjournald starting.  Commit interval 5 seconds
[   15.622622] EXT3 FS on sde1, internal journal
[   15.622628] EXT3-fs: mounted filesystem with ordered data mode.
[   16.083713] type=1505 audit(1247198429.581:2): operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" name2="default" pid=2204
[   16.134528] type=1505 audit(1247198429.633:3): operation="profile_load" name="/sbin/dhclient-script" name2="default" pid=2208
[   16.134676] type=1505 audit(1247198429.633:4): operation="profile_load" name="/sbin/dhclient3" name2="default" pid=2208
[   16.134726] type=1505 audit(1247198429.633:5): operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" name2="default" pid=2208
[   16.134771] type=1505 audit(1247198429.633:6): operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" name2="default" pid=2208
[   16.182174] type=1505 audit(1247198429.681:7): operation="profile_load" name="/usr/bin/freshclam" name2="default" pid=2213
[   16.214858] type=1505 audit(1247198429.713:8): operation="profile_load" name="/usr/sbin/clamd" name2="default" pid=2217
[   16.353006] type=1505 audit(1247198429.853:9): operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" name2="default" pid=2221
[   16.353205] type=1505 audit(1247198429.853:10): operation="profile_load" name="/usr/sbin/cupsd" name2="default" pid=2221
[   16.399133] type=1505 audit(1247198429.897:11): operation="profile_load" name="/usr/sbin/dhcpd3" name2="default" pid=2225
[   36.411219] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   36.411222] Bluetooth: BNEP filters: protocol multicast
[   36.469511] Bridge firewalling registered
[   37.995110] pci 0000:01:05.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[   38.124877] warning: `dhcpd3' uses 32-bit capabilities (legacy support in use)
[   38.282170] [drm] Initialized drm 1.1.0 20060810
[   38.411635] [drm] Initialized radeon 1.29.0 20080528 on minor 0
[   39.190714] [drm] Setting GART location based on new memory map
[   39.191230] [drm] Loading RS690/RS740 Microcode
[   39.191248] [drm] Num pipes: 1
[   39.191254] [drm] writeback test succeeded in 1 usecs
[   45.502014] r8169: eth0: link up
[   45.502022] r8169: eth0: link up
[   56.304014] eth0: no IPv6 routers presentHere is the attempted assembly of the array and the resulting fdisk -l scenario
> n5oe@ubuntu-server:~$ sudo mdadm -A /dev/md0
mdadm: no devices found for /dev/md0
n5oe@ubuntu-server:~$ cat /proc/mdstat
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10] 
md_d0 : inactive sdc[0](S)
      976762496 blocks
       
unused devices: <none>
n5oe@ubuntu-server:~$ sudo mdadm --assemble --scan
mdadm: no devices found for /dev/md0
/dev/md0: File exists
mdadm: /dev/md/0 has been started with 1 drive (out of 2).
n5oe@ubuntu-server:~$ fdisk -l
n5oe@ubuntu-server:~$ sudo fdisk-l
sudo: fdisk-l: command not found
n5oe@ubuntu-server:~$ sudo fdisk -l

Disk /dev/sda: 61.4 GB, 61492838400 bytes
255 heads, 63 sectors/track, 7476 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x90909090

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        7165    57552831   83  Linux
/dev/sda2            7166        7476     2498107+   5  Extended
/dev/sda5            7166        7476     2498076   82  Linux swap / Solaris

Disk /dev/sdb: 61.4 GB, 61492838400 bytes
255 heads, 63 sectors/track, 7476 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x43de2278

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        7476    60050938+  83  Linux

Disk /dev/sdc: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000

Disk /dev/sdc doesn't contain a valid partition table

Disk /dev/sdd: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000

Disk /dev/sdd doesn't contain a valid partition table

Disk /dev/sde: 60.0 GB, 60022480896 bytes
255 heads, 63 sectors/track, 7297 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x90909090

   Device Boot      Start         End      Blocks   Id  System
/dev/sde1               1        7297    58613121   83  Linux

Disk /dev/md0: 1000.2 GB, 1000204795904 bytes
2 heads, 4 sectors/track, 244190624 cylinders
Units = cylinders of 8 * 512 = 4096 bytes
Disk identifier: 0x00000000

Disk /dev/md0 doesn't contain a valid partition table
n5oe@ubuntu-server:~$ 
n5oe@ubuntu-server:~$ sudo mount /dev/sdd /media/1TBRaid1Array
[sudo] password for n5oe: 
mount: unknown filesystem type 'linux_raid_member'
n5oe@ubuntu-server:~$ sudo mount -t ext3 /dev/sdd /media/1TBRaid1Array
mount: /dev/sdd already mounted or /media/1TBRaid1Array busy
n5oe@ubuntu-server:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1              55G   17G   35G  33% /
tmpfs                 930M     0  930M   0% /lib/init/rw
varrun                930M  396K  930M   1% /var/run
varlock               930M     0  930M   0% /var/lock
udev                  930M  168K  930M   1% /dev
tmpfs                 930M     0  930M   0% /dev/shm
lrm                   930M  2.5M  928M   1% /lib/modules/2.6.28-13-generic/volatile
/dev/sdb1              57G   49G  5.2G  91% /media/60gBackup
/dev/sde1              56G  9.7G   43G  19% /media/60gBackup2It says I have 1/2 of an array but it will not mount or show up in the df -h page. 
This was about my 5th or 6th total rebuild on an attempted Raid1 array. None of which come back after a server reboot.

Please any ideas on what I am missing on the partitioning or something?
Thanks
n5oe

---

### Post by dschuett on 2009-07-25
I have been working for days with your same problem, I have tried every variation that you have. I also tried to user the partition name instead of the drive name, which i came across in another thread. so instead of mdadm --create /dev/md0 ....... /dev/sdb /dev/sdc
i tried mdadm --create /dev/md0 ............... /dev/sdb1 /dev/sdc1 

Still with no luck. I get the RAID setup up fine, but as soon as i reboot my mount is gone. The folder is there, but with none of my media in it. and it is not showing my 2TB size. I have sent days an nights trying to get my linux server running but its impossible to do so with out my RAID storage.

Has ANYONE figures this out yet???

---

### Post by n5oe on 2009-07-26
I did not get it figured out and had no more responses with suggestions. I had to come up with something so took the LONG way around, rebuild server from scratch. This may not be an option for you, but I took this route and simply built 2 servers during the process.

I installed Ubuntu 9.04 server edition from scratch on 2x160gig drives raid1 successfully by following this page[html] http://usefulubuntu.blogspot.com/2009/03/raid-1-and-ubuntu-server-810.html[/html] it worked just fine with no problems at all. This was the actual server rebuild, I then opted to simply make a dedicated file server on another machine following the same instructions but this time using the 2x1tb drives. Installed Samba and Proftp for access.

I personally took this route for a few reasons, (1) I probably would have lost data anyway with continually using fdisk and gparted over and over on the system drives. (2) Timewise it would have been faster to do this had I known the trouble I was having in the precedding post.

The only other thing I wish I had tried was trying the alternate install cd as suggested on other sites, but the main server needed larger hard drives anyway, so I opted to go this route.

---

### Post by Drunken on 2009-07-26
I get the same problem, after creating working /dev/md0, after a reboot it disappears!
This is on a clean ubuntu 9 install too.

---

### Post by nex9 on 2009-08-01
Please file this as a bug! I had the same problem - if enough people complain maybe someone will fix it! I gave up on ubuntu raid and moved to CentOS - worked perfectly.

---

### Post by Drunken on 2009-08-02
I got it working.
After creating the raid (and before rebooting), run this command:
```

#cd /etc/mdadm
#mdadm --examine --scan --config=mdadm.conf >> mdadm.conf

```

This will save the raid you created to the end of your config file, and this does work!
You can now reboot and run
```
#cat /proc/mdstat
```
and it should be listed as active.

---

### Post by sx_fusion on 2010-03-21
Hi,

Yeah so that doesn't work for me, I just get a "Premission Denied" error (eventhough I'm using sudo).

everything works perfect till reboot.

any other ideas?

Thanks,

Lu

---

### Post by sx_fusion on 2010-03-21
Hi... again,

I tried defining the UUID in the mdadm.conf and that seemed to work. It's now

```
# mdadm.conf
#
# Please refer to mdadm.conf(5) for information about this file.
#

# by default, scan all partitions (/proc/partitions) for MD superblocks.
# alternatively, specify devices to scan, using wildcards if desired.
DEVICE /dev/sdb /dev/sdc

# auto-create devices with Debian standard permissions
CREATE owner=root group=disk mode=0660 auto=yes

# automatically tag new arrays as belonging to the local system
HOMEHOST <system>

# instruct the monitoring daemon where to send mail alerts
MAILADDR root

# definitions of existing MD arrays
**ARRAY /dev/md0 uuid=a52c1aad:8fde9b29:bd4932e8:3299a73b level=0 devices=/dev/sdb,/dev/sdc**

# This file was auto-generated on Mon, 22 Mar 2010 00:06:15 +1300
# by mkconf $Id$

```Hopefully that helps someone.

---

### Post by nitroboost on 2011-05-04
Just wanted to follow up and resurrect this thread as this is one of the top google hits and it doesn't have the complete fix.

The issue for most of you will be that the raid was created post install, so to rehash, first make sure the output of mdadm --examine --scan exists at the bottom of your /etc/mdadm/mdadm.conf

2nd, and this is the part most people miss that causes the most trouble, you need to run 'update-initramfs -k all -u' to get that new mdadm.conf into your ramdisk, especially if your raid is your root disk.  This update-initramfs applies if your raids UUID changes for whatever reason as mine did from sysrcd mangling it etc.

---

