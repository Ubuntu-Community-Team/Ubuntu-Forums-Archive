---
title: "Failed software RAID array"
date: 2009-06-23
forum: Hardware
---

### Post by kmdougla on 2009-06-23
Hi all,
I recently setup a software RAID array with two 160 GB SATA2 hard drives. Ubuntu is currently installed on a separate 250 GB hard drive so that the RAID array is only used as storage. After rebooting the system, I received the following error:

```
Log of fsck -C3 -R -A -a 
Tue Jun 23 07:42:23 2009

fsck 1.41.4 (27-Jan-2009)
/dev/sda1: clean, 31/24096 files, 23153/96356 blocks
fsck.ext3: No such file or directory while trying to open /dev/md0

/dev/md0: 
The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>

fsck died with exit status 8
```My /etc/fstab:

```
# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda3 during installation
UUID=f11a7061-e70a-4708-99ee-5c718b0282cd /               ext4    relatime,errors=remount-ro 0       1
# /boot was on /dev/sda1 during installation
UUID=d5822948-0e63-4b47-8c3a-930621b4ecce /boot           ext3    relatime        0       2
# swap was on /dev/sda2 during installation
UUID=639a64d5-a766-4610-abda-490eb2d65705 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0 0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0 0
/dev/md0    /mnt/storage    ext3    defaults    1 2
```And the output of sudo fdisk -l

```
Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x290b290b

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          12       96358+  83  Linux
/dev/sda2              13         620     4883760   82  Linux swap / Solaris
/dev/sda3             621       30401   239215882+  83  Linux

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0006effc

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       19457   156288321   fd  Linux raid autodetect

Disk /dev/sdc: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x01e58ed3

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       19457   156288321   fd  Linux raid autodetect
```Could anyone clarify what exactly the problem is and how I can get the array working again? It worked after I set it up initially, but now Ubuntu boots with the error given above. Thanks.

---

### Post by kdkirsch on 2009-06-24
Hi. I am having the same problem. I have a 2 disk software raid 1 array that I setup using mdadm. Both disks are formatted ext4. The array was running fine until 2 or so days ago, when after updating per the Update Manager and performing a mandatory reboot, my machine halted with:
```
* Checking file systems...
151
fsck 1.41.4 (27-Jan-2009)
fsck.ext4: No such file or directory while trying to open /dev/md0
/dev/md0:
The superblock could not be read or does not describe a correct ext2
filesystem. If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
e2fsck -b 8193 <device>

fsck died with exit status 8
[fail]
```

The log file (/var/log/fsck/checkfs) repeats the same info as above.

My array is composed of /dev/sdb and /dev/sdc.

The abbreviated output of sudo fdisk -l is:

```
...
Disk /dev/sdb: 80.0 GB, 80000000000 bytes
255 heads, 63 sectors/track, 9726 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000

Disk /dev/sdb doesn't contain a valid partition table

Disk /dev/sdc: 80.0 GB, 80000000000 bytes
255 heads, 63 sectors/track, 9726 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000

Disk /dev/sdb doesn't contain a valid partition table
...
```

I'm not sure how to access the update logs but if someone tells me what to do, I will post the output to help resolve this problem. Thanks!

---

### Post by kmdougla on 2009-06-27
I tried printing the available alternate superblocks, but my system does not seem to even have the newfs program.

```
sudo newfs -N /dev/sdb1
bash: newfs: command not found
```This pretty much stumps me. Can anyone offer any suggestions on where to go from here?

My kernel is: 2.6.28-13-generic and I am running Ubuntu 9.04. Thanks!

---

### Post by kmdougla on 2009-06-27
I've made some progress.

I used mke2fs to display the available alternate superblocks on the drives. I then used e2fsck to switch to the alternate superblock (32768 in this case). 

[SIZE=3]**Several posts from other forums stressed the -n option in mke2fs; without it, your file system could be erased.**[/SIZE]

```
sudo su
mke2fs -n /dev/sdb1
e2fsck -b 32768 /dev/sdb1
```/dev/sdc1 was busy because (I think) /dev/md0 (my RAID device) was still attached to it. I stopped it using

```
mdadm --fail /dev/md0
mdadm --stop /dev/md0
```.

Then, I repeated the first two steps on /dev/sdc1. Following this, I rebuilt the array and wrote the mdadm.conf file:

```
mdadm --assemble /dev/md0 /dev/sdb1 /dev/sdc1
mdadm --detail --scan --verbose > /etc/mdadm.conf
```Finally, I mounted the RAID array (it was already in my /etc/fstab file, so the -a option was sufficient).

```
mount -a
```This gave me access to the files on my array. However, upon rebooting the system, the same problem occurred while loading Ubuntu, i.e. the superblock was bad. I am still open to any suggestions on a solution. Thanks, as always.

---

### Post by kmdougla on 2009-07-01
I now have a working array that gives me no issues when I boot. I'm not sure what happened, and my solution almost certainly is not elegant, but here's what I did:

I reconstructed the array as detailed in a previous post and copied my data to my primary hard drive. Then I stopped the array using

```
sudo mdadm --stop /dev/md0
```Next, I completely zero'ed the hard drives. Use caution with this command; you don't want to zero any primary hard drives/paritions/system files.

```
sudo dd if=/dev/zero of=/dev/sdb
```I did this with both drives. It took a couple of hours for each one.

Next, instead of using fdisk to format them, I used gparted. gparted first established an MS-DOS partition table on the drives(I'm not sure what this does). Then, I formatted them with the linux raid file system (in gparted). I used mdadm to create the array from scratch and let the drives resync. Finally, I formatted the new /dev/md0 with the ext3 filesystem and mounted the drive.

I'm not quite sure why this worked, but I think my problem came from the fact that I had a previous issue with the two drives belonging to a raid array on the JMicron controller on my ABit AB9 motherboard. I had to zero the superblocks in order to remove the memory of this previous array, but the usual s**udo mdadm --zero-superblock /dev/sdb** did not work, so I used the dd command as above. After I did this, I formatted them with a linux raid system using fdisk. fdisk might have neglected to setup the MS-DOS partition table that I mentioned gparted did.

I hope this helps other people who might have similar issues. I'm also open to any suggestions as to what the problem may have actually been.

---

### Post by boomboom69 on 2009-11-16
I'm looking for some help with my server. I installed ubuntu 9.04 server amd64 edition. I have 4 HDD with 3 partitions each and all of them raided. I set the 1st partitions, md0, as raid1 and is mounted /boot. Then the second partitions, md1, as raid10 and mounted /. Finally the third partitions, md2, as raid10 and mount as swap. I never set the commands for booting into a degraded array. We recently had a power failure out here and caused the system to lock up. After I got it to reboot by pulling the power cable, it loads the grub and starts the kernel. When it tries to load the root partition it gives errors about super block being bad and says it tried to mount it as several different files systems and failed and then just hangs there. Selecting recovery mode gives same thing. 

The error displayed is:
md: md1: raid array is not clean -- starting background reconstruction
EXT3-fs: unable to read superblock
EXT4-fs: unable to read superblock
kernel panic - not syncing: VFS: unable to mount root fs on unknown block - block(9,1)

Is there a grub kernel option I can add to get it to boot a degraded array? Or how else would this be fixed?

---

### Post by santhony on 2009-11-17
I just found and fixed my problems after 3 days of scrubbing.....

My MDADM Raid 5 partitions, on two of the member disks, just mysterously disappeared.

I have a 7 disk Raid 5 Array.  After system updates and a reboot.  Two of my drives no longer had their partitions showing.  

GParted did show the two drives as intact, that they were members of a raid array.  

fdisk -l also showed the drives correctly with their partitions.

BUT, the disk Utility, Palimpseset showed the two drives with no partition table.

The FIXX:  REMOVE DMRAID.

After unistalling DMRAID using the Synaptic Package Manager... The drives all of a sudden showed up correctly and assembled all on their own..

Wall Lah..  

I hope this helps anyone with the same situation.

Good Luck and please post any tricks or tips you find!!

---

### Post by burpen on 2010-01-28
> **santhony said:**
> fdisk -l also showed the drives correctly with their partitions.

BUT, the disk Utility, Palimpseset showed the two drives with no partition table.

The FIXX:  REMOVE DMRAID.

After unistalling DMRAID using the Synaptic Package Manager... The drives all of a sudden showed up correctly and assembled all on their own..

Wall Lah..  

I hope this helps anyone with the same situation.

Good Luck and please post any tricks or tips you find!!

Thank you *so* much! I had a very similar problem, and I'll give a list of "symptoms" to help anyone else find this solution.

[LIST]
[*]I had extra entries in my fstab looking like /dev/nvidia/something that I had never seen before. These were duplicate entries for partitions on another disk.
[*]fdisk -l showed the missing partitions (/dev/sdb1 and /dev/sdb3) correctly.
[*]Palimpsest did not display the partitions at all (said entire disk at /dev/sdb was unformatted).
[*]GParted showed the partitions but complained of bad superblocks. I could not repair or do anything with them at this point.
[*]I tried e2fsck -b 32768 /dev/sdb1 to restore the superblocks but it returned "no such file or directory". Also tried a multitude of other things to this end, all resulting in either a "no such file" or "resource busy".
[*]Upon further inspection, /dev/sdb was present but /dev/sdb1 and /dev/sdb3 were missing.
[/LIST]

To fix: I added entries to fstab for the partitions but they did not both appear until I removed the dmraid package as per santhony's advice.

After removing dmraid, the erroneous /dev/nvidia paths went away and /dev/sdb3 reappeared immediately and GParted checked it just fine. I still didn't see /dev/sdb1, so I rebooted. It then appeared and was no longer inaccessible to GParted, and I successfully repaired the partition.

Now all is well (for the time being).

---

### Post by artships on 2010-04-05
My problem has been a little more difficult.  I have a Karmic server so everything has to be commandline (no gparted).  And, it won't do software RAID1.

I slipped both 2TB Samsung drives into a 64-bit Karmic desktop, used gparted to give them each a single **ext4** partition over an MSDOS file system.  

Plucked them and put them into a 32 bit Karmic server running off some other PATA drive. **sudo fdisk -l** shows:
```
   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1      243201  1953512001   83  Linux

Disk /dev/sdb: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00007f23
```
/dev/sdb1 is the same.

Time to make RAID:
```
sudo mdadm --create --verbose /dev/md0 --level=1 --raid-devices=2 /dev/sda1 /dev/sdb1
mdadm: /dev/sda1 appears to contain an ext2fs file system
    size=1953512000K  mtime=Wed Dec 31 18:00:00 1969
mdadm: Cannot open /dev/sdb1: Device or resource busy
mdadm: create aborted
```

As another thread suggested, I changed the permissions to /etc/mdadm/mdadm.conf so that I could write to it...
 **sudo mdadm --examine --scan --config=mdadm.conf >> /etc/mdadm/mdadm.conf**
Which appended to mdadm.conf the line:
```
ARRAY /dev/md0 level=raid1 num-devices=2 UUID=ad9a81f4:be7e3d25:57fa4b79:883376bb
```
I've read nothing that says **ext4** is only for 64-bit machines, and in fact, the PATA drive in the server is formatted ext4.  Is it because the MB is a bog-standard DFI LANParty UT nF3 250Gb?  It has FakeRaid, but I'm not using it. Nor am I using dmraid.

Found a fix - [http://en.wikipedia.org/wiki/Mdadm#Known_problems](http://en.wikipedia.org/wiki/Mdadm#Known_problems) - I had to "zero the superblock."

Then I followed most of [http://www.howtoforge.com/software-raid1-grub-boot-debian-etch](http://www.howtoforge.com/software-raid1-grub-boot-debian-etch).  So now **fdisk -l** shows:
```
Disk /dev/sda: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000ee015

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1      243201  1953512001   fd  Linux raid autodetect
```
**cat /proc/mdstat** shows:
```
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10] 
md0 : active raid1 sda1[0] sdb1[1]
      1953511936 blocks [2/2] [UU]
      [==>..................]  resync = 11.1% (217634176/1953511936) finish=267.9min speed=107987K/sec
      
unused devices: <none>
```
In 267 minutes I'll execute **mkfs.ext4 /dev/md0** and I'll be done.

---

