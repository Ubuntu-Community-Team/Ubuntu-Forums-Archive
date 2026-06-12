---
title: "Upgrading a 500Gb main drive to a 1Tb drive"
date: 2016-03-06
forum: Hardware
---

### Post by Curbie on 2016-03-06
I'm trying to upgrade a 500Gb main drive to a brand new 1Tb drive, the 500 Gb drive is older, but still functions fine, I just like to maintain multiple backups (I have 3x500 Gb drives 1 with Xubuntu 12.??, 1 with Xubuntu 14.04, and 1 with data) so if a hard drive goes down I can easily recover, and I just upgraded from Xubuntu 12.?? to Xubuntu 14.04.
 

 I used Clownzilla to clown the 500Gb drive to the 1Tb drive, then replaced the 500Gb drive with the 1Tb drive and all was well except the new 1Tb drive had 1 500Gb partition with 500Gb of unallocated space. I then used gpart to create a new partition for the unallocated space, but the new partition apparently is supposed to have root ownership and I couldn't write write to it.
 

 I was attempting to try this plan:

 sudo mkdir /media/curbie/DataCurbie/Data
 sudo umount /dev/sdb3
 sudo mount /dev/sdb3 /media/curbie/DataCurbie/Data
 chown -R curbie:curbie /media/curbie/DataCurbie/Data


 based on this mount listing:
 curbie@curbie-desktop:~$ mount 
 /dev/sda1 on / type ext4 (rw,errors=remount-ro) 
 proc on /proc type proc (rw,noexec,nosuid,nodev) 
 sysfs on /sys type sysfs (rw,noexec,nosuid,nodev) 
 none on /sys/fs/cgroup type tmpfs (rw) 
 none on /sys/fs/fuse/connections type fusectl (rw) 
 none on /sys/kernel/debug type debugfs (rw) 
 none on /sys/kernel/security type securityfs (rw) 
 udev on /dev type devtmpfs (rw,mode=0755) 
 devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620) 
 tmpfs on /run type tmpfs (rw,noexec,nosuid,size=10%,mode=0755) 
 none on /run/lock type tmpfs (rw,noexec,nosuid,nodev,size=5242880) 
 none on /run/shm type tmpfs (rw,nosuid,nodev) 
 none on /run/user type tmpfs (rw,noexec,nosuid,nodev,size=104857600,mode=0755) 
 none on /sys/fs/pstore type pstore (rw) 
 systemd on /sys/fs/cgroup/systemd type cgroup (rw,noexec,nosuid,nodev,none,name=systemd) 
 gvfsd-fuse on /run/user/1000/gvfs type fuse.gvfsd-fuse (rw,nosuid,nodev,user=curbie) 
 /dev/sda3 on /media/curbie/DataCurbie type ext4 (rw,nosuid,nodev,uhelper=udisks2) 
 

 sudo mkdir /media/curbie/DataCurbie/Data
 Was successful, and created a directory
 sudo umount /dev/sdb3
 produced this:
 curbie@curbie-desktop:~$ sudo umount /dev/sdb3 
 [sudo] password for curbie:  
 umount: /dev/sdb3: not found
 

 I don't know what I'm doing wrong or even if this plan is proper for upgrading to a new hard drive?

 

 Any help wound be appreciated.
 

 Curbie

---

### Post by weatherman2 on 2016-03-06
FYI, if you'd prefer to have just one 1TB partition instead of two 500GB partitions, use Gparted to grow your existing partition to use all 1TB.  But you will need to do this by booting a live USB (or disc) Ubuntu because you can't resize an active, booted partition.  Resizing should be easy and quick, and now is the time to do it.

Of course, that means you can't use your 500GB as a pure backup anymore, because it will be too small to fit everything from a 1TB drive.  There are pros and cons of having separate partitions vs. one big one, and if you choose to have two separate that's OK as long as you realize how easy it is to do right now.  It's much harder to do once you start saving data on the new partition!  The big "con" of two separate partitions is that if you fill one up and the other has plenty of free space, it's hard to balance one to give space to the other.

In the future, consider LVM for a clean install.  This gives you more sophisticated control over partition sizes and even lets you spread a logical volume (one partition) over several hard drives if you want to!

---

### Post by weatherman2 on 2016-03-06
And by the way, it looks like you no longer have /dev/sdb (second hard drive) installed, so now your 1TB drive is /dev/sda .  To unmount that partition, you'd do:

```
sudo umount /dev/sda3
```

---

### Post by oldfred on 2016-03-06
I think once you have mounted it, then it is not sda3 anymore, but your mount

dev/sda3 on /media/curbie/DataCurbie type ext4 (rw,nosuid,nodev,uhelper=udisks2)

Have you given yourself ownership and permissions?

I normally mount at /mnt/data and link folders into /home

 # is comment, do not type
sudo parted -l
sudo mkdir /mnt/data
sudo mount /dev/sda5 /mnt/data
#where sda5 needs to be your drive, partition
sudo chmod -R a+rwX,o-w /mnt/data
# Note that the -R is recursion and everything is changed, do NOT run on any system partitions.
#All directories will be 775.
#All files will be 664 except those that were set as executable to begin with.
sudo chown -R $USER:$USER /mnt/data 

Just change above to 
sudo chmod -R a+rwX,o-w /media/curbie/DataCurbie
sudo chown -R $USER:$USER /media/curbie/DataCurbie

Note that -R is recursion, and all lower level folders/files are also changes. Never, ever run on system partition, just data partitions that you can own.

---

### Post by Curbie on 2016-03-06
OldFred,
 
 Thanks for the reply.
 
 “I think once you have mounted it, then it is not sda3 anymore, but your mount

dev/sda3 on /media/curbie/DataCurbie type ext4 (rw,nosuid,nodev,uhelper=udisks2)”
 
 I'm sorry but I haven't played with the configuration of a Unix type OS since the 70's, I can vaguely recall what some things are, but I don't really know how to answer this, other than the drive probably was mounted when I ran the mount terminal command.

“Have you given yourself ownership and permissions?”
 
 Didn't get to that, I thought that the mount came first and I'm still struggling doing that.

“I normally mount at /mnt/data and link folders into /home”
 
 I don't know what that means or where to read on how to do that?

“# is comment, do not type
sudo parted -l
sudo mkdir /mnt/data
sudo mount /dev/sda5 /mnt/data
#where sda5 needs to be your drive, partition
sudo chmod -R a+rwX,o-w /mnt/data
# Note that the -R is recursion and everything is changed, do NOT run on any system partitions.
#All directories will be 775.
#All files will be 664 except those that were set as executable to begin with.
sudo chown -R $USER:$USER /mnt/data 

Just change above to 
sudo chmod -R a+rwX,o-w /media/curbie/DataCurbie
sudo chown -R $USER:$USER /media/curbie/DataCurbie”
 
Is that an example, or actual commands to be used after I figure out the “I normally mount at /mnt/data and link folders into /home” thing?

Curbie

---

### Post by Bucky Ball on 2016-03-07
Clownzilla. I like that. But don't you mean Clonezilla? Clownzilla sounds like a freak-show clown!

---

### Post by Curbie on 2016-03-07
Bucky Ball,

   Clownzilla is what happens to goofy names that I've only spelled or thought about twice ever, but with two years in between. I'm lucky to remember my phone number because I don't call myself and therefor don't use it either. Maybe being older than dust has something to do with also?

Curbie

---

### Post by oldfred on 2016-03-07
All the references to /mnt/data and linking is how I do it.
I thought you had already mounted it to /media/curbie/DataCurbie, so the second set was what I thought would be your command without having to edit my typical commands usinig /mnt/data.

       The actual user settings are small. My /home is 2GB with most of that as .wine with Picasa which I have not yet moved to my /data. Because /home is small I now keep it as part of / (root) which is a total of 11GB with /home.
Then I can have a fully functioning system on one drive but have data linked in from other partitions on other drives. 
   Data can be shared without the possible conflicts of user settings being different in different versions. I only copy some settings from one install to the next, normally. But I have to separately back up /home and the /data partition. Also saves the error of reformating a /home partition accidentally. I never reformat my /data and just configure / for install. 
   [http://ubuntuforums.org/showthread.php?t=2315714](http://ubuntuforums.org/showthread.php?t=2315714)
Splitting home directory discussion and details:
[http://ubuntuforums.org/showthread.php?t=1811198](http://ubuntuforums.org/showthread.php?t=1811198)
[http://ubuntuforums.org/showthread.php?t=1901437](http://ubuntuforums.org/showthread.php?t=1901437)
[http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata](http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata)

---

### Post by Curbie on 2016-03-07
After spending the day reading the posts and related linked posts, to try to get a handle the mount portion and overview of OldFred's procedure, I'm worried that I'm building that procedure on a shaky foundation (an improperly configured drive) and since I'm cloning my original drive setup, I would be cloning any misconfiguration with that original drive setup to this newer and future drives.


I found and ran the following information gathering commands just to see if I could put together some of their relationships and glean and information. Could someone please give that a once over to see if my drive configurations are sound before I go on to mount/symlinks?


Curbie

```

curbie@curbie-desktop:~$ sudo fdisk -lu 
[sudo] password for curbie: 

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes 
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors 
Units = sectors of 1 * 512 = 512 bytes 
Sector size (logical/physical): 512 bytes / 4096 bytes 
I/O size (minimum/optimal): 4096 bytes / 4096 bytes 
Disk identifier: 0x0000f390 

Device Boot Start End Blocks Id System 
/dev/sda1 * 2048 960522239 480260096 83 Linux 
/dev/sda2 960524286 976771071 8123393 5 Extended 
Partition 2 does not start on physical sector boundary. 
/dev/sda3 976771072 1953523711 488376320 83 Linux 
/dev/sda5 960524288 976771071 8123392 82 Linux swap / Solaris 

Disk /dev/sdb: 500.1 GB, 500107862016 bytes 
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors 
Units = sectors of 1 * 512 = 512 bytes 
Sector size (logical/physical): 512 bytes / 4096 bytes 
I/O size (minimum/optimal): 4096 bytes / 4096 bytes 
Disk identifier: 0x00000000 

Disk /dev/sdb doesn't contain a valid partition table
```

```

curbie@curbie-desktop:~$ sudo blkid -c /dev/null -o list 
[sudo] password for curbie: 
device fs_type label mount point UUID 
------------------------------------------------------------------------------- 
/dev/sda1 ext4 / 1ef20c10-da27-47c6-b744-46a1477a1313 
/dev/sda3 ext4 DataCurbie /media/curbie/DataCurbie 3951f0f4-c40a-4d00-bab9-e5b54b6ef4be 
/dev/sda5 swap <swap> fc427b57-d9a8-4ed7-955d-b20513d0ddf3 
/dev/sdb ext4 data /media/curbie/data ec1693e9-bb02-4c01-97ee-833bdd76325a
```

```

curbie@curbie-desktop:~$ mount 
/dev/sda1 on / type ext4 (rw,errors=remount-ro) 
proc on /proc type proc (rw,noexec,nosuid,nodev) 
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev) 
none on /sys/fs/cgroup type tmpfs (rw) 
none on /sys/fs/fuse/connections type fusectl (rw) 
none on /sys/kernel/debug type debugfs (rw) 
none on /sys/kernel/security type securityfs (rw) 
udev on /dev type devtmpfs (rw,mode=0755) 
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620) 
tmpfs on /run type tmpfs (rw,noexec,nosuid,size=10%,mode=0755) 
none on /run/lock type tmpfs (rw,noexec,nosuid,nodev,size=5242880) 
none on /run/shm type tmpfs (rw,nosuid,nodev) 
none on /run/user type tmpfs (rw,noexec,nosuid,nodev,size=104857600,mode=0755) 
none on /sys/fs/pstore type pstore (rw) 
systemd on /sys/fs/cgroup/systemd type cgroup (rw,noexec,nosuid,nodev,none,name=systemd) 
gvfsd-fuse on /run/user/1000/gvfs type fuse.gvfsd-fuse (rw,nosuid,nodev,user=curbie) 
/dev/sda3 on /media/curbie/DataCurbie type ext4 (rw,nosuid,nodev,uhelper=udisks2) 
/dev/sdb on /media/curbie/data type ext4 (rw,nosuid,nodev,uhelper=udisks2)
```

```
 
curbie@curbie-desktop:~$ sudo cat /etc/fstab 
[sudo] password for curbie: 
# /etc/fstab: static file system information. 
# 
# Use 'blkid' to print the universally unique identifier for a 
# device; this may be used with UUID= as a more robust way to name devices 
# that works even if disks are added and removed. See fstab(5). 
# 
# <file system> <mount point> <type> <options> <dump> <pass> 
proc /proc proc nodev,noexec,nosuid 0 0 
# / was on /dev/sda1 during installation 
UUID=1ef20c10-da27-47c6-b744-46a1477a1313 / ext4 errors=remount-ro 0 1 
# swap was on /dev/sda5 during installation 
UUID=fc427b57-d9a8-4ed7-955d-b20513d0ddf3 none swap sw 0 0
```

---

### Post by oldfred on 2016-03-08
It is shown mounted at /media/curbie/data which is different than /media/curbie/DataCurbie. Case is very important in Linux and I have labeled partitions Data and mounted at data and gotten confused.

And you do not show it in fstab. So I presume you clicked on it in Nautilus to automount it with udisks.
If using for linking data into /home you need to mount in fstab so data is automatically there when you reboot.
Default mounts by Nautilus use label if available or UUID, but you have to do that. And they are considered temporary mounts and use /media. 

There are many discussions on using /mnt or /media for permanent mounts. And Linux Standard Base is not exactly clear. But I use /mnt for my internal drive partitions and let system use /media/fred for external flash drives.
You can use what ever you want, but need to be consistent.

So first create permanent mount in fstab.
 [http://ubuntuforums.org/showthread.php?t=1983336](http://ubuntuforums.org/showthread.php?t=1983336)
Mount & edit fstab from user Morbius1 in Post # 6 - suggest using templates instead.
Good example of manually mounting, except I prefer /mnt/xxx as location to mount to. 

 fstab entry For ext4, copy & paste into fstab with correct UUID & mount point:
UUID=076426af-cbc5-4966-8cd4-af0f5c879646 /media/Data ext4 defaults,noatime 0 2 
   ** You will have to create the mount point yourself, for example:
sudo mkdir /media/WinD
and/or 
sudo mkdir /media/Data

 ** To find the correct UUID for your partitions:
sudo blkid -c /dev/null -o list
** Then add the template with the correct UUID and mount point to fstab:
sudo cp /etc/fstab /etc/fstab.backup
gksu gedit /etc/fstab
** And when you are done editing fstab and saving it run the following command to test for errors and mount the partitions without requiring a reboot. You will know before you reboot if something is amiss. Make sure you have partition unmounted if previously mounted:
sudo mount -a 

This is my current entry:
```
# Entry for /dev/sdb4 :
UUID=f9537995-8b44-4abb-b5fb-ec27023f57b2 /mnt/data ext4 relatime 0 2

```

See this for explanation of relatime
man mount

---

### Post by Curbie on 2016-03-08
OldFred,
  
  Thanks for the reply. I apologize for screwing things up so badly that it's fooling the master, which tells me that I first need to fix existing configuration issues as NOT to attempt to build on them further. It shows just how robust xUbuntu is, that it will run flawlessly for years misconfigured.
  
  What I know is, that when I made the transition from Win a couple of years ago I bought new hardware for xUbuntu, of importance here is two 500Gb hard drives, leaving the original Win 500Gb drive untouched, so I could use the new 500Gb drives to test dual boot xUbuntu and Win AND single boot with VirtualBox running Win, I chose single boot with VirtualBox running Win.
  
  So the configuration I've running for years had been one 500Gb drive for xUbuntu, programs, and data, AND a second 500Gb drive marked “data” for data and backups.  
  
  The new configuration, is one 1000Gb drive with two 500Gb partitions, one 500Gb partition for xUbuntu, programs, and data, AND one 500Gb partition labelled “DataCurbie” to copy the contents of the 500Gb drive labelled “data” from.  When the data is copied from the 500Gb drive labelled “data”, to the 500Gb partition labelled “DataCurbie” I can remove the 500Gb drive labelled “data” and keep an off-site  500Gb drive for xUbuntu, programs, and data, AND an off-site 500Gb drive for data.

  I know, backup overkill, but I still have everything I've ever written in 40 years, and this 100's of Gb of data isn't videos and games, so the backup overkill scheme has worked in every circumstance that has been thrown at it over 40 years, drive failures, virus, and mistakes, anything, although, I haven't yet had to recover from fire or theft, but with my luck...
  
  “data” is a 500Gb drive, and “DataCurbie” is the second 500Gb partition of the 1000GB drive, labelled differently to avoid confusion for the copy. It's clear to me that I first need to correct existing configuration issues, but I think I can use your posts to do that before moving on.

  As if you already didn't suspect what a moron your dealing with, I've baan making notes on every option of every command you've posted by researching the Internet looking for the info that the “man” command returns (if it works for all or most commands), that one jewel will save me hours/days, it seemed like I had to read half the Internet for every option of every command posted to understand it.
  
  Thank you so much for all the time and patience you've spent helping a stranger. I need to switch gears to first correct my current misconfiguration issues and I'll need to come with a plan to do that.

  Curbie

---

### Post by Curbie on 2016-03-08
So checking my drives:
  ```
blkid -c /dev/null -o list
 device     fs_type label    mount point    UUID 
 ------------------------------------------------------------------------------- 
 /dev/sda1  ext4             /              1ef20c10-da27-47c6-b744-46a1477a1313 
 /dev/sda3  ext4    DataCurbie /media/curbie/DataCurbie 3951f0f4-c40a-4d00-bab9-e5b54b6ef4be 
 /dev/sda5  swap             <swap>         fc427b57-d9a8-4ed7-955d-b20513d0ddf3 
 /dev/sdb   ext4    data     /media/curbie/data ec1693e9-bb02-4c01-97ee-833bdd76325a 
```
 
 therefor:
 1000Gb new drive
     ...500Gb partition one
        ....../dev/sda1  ext4             /              1ef20c10-da27-47c6-b744-46a1477a1313 
     ...500Gb partition two
        ....../dev/sda3  ext4    DataCurbie /media/curbie/DataCurbie 3951f0f4-c40a-4d00-bab9-e5b54b6ef4be
 500Gb second drive labelled “data”
     ...500Gb only partition
        ....../dev/sdb   ext4    data     /media/curbie/data ec1693e9-bb02-4c01-97ee-833bdd76325a 
 
checking what's mounted:
 ```
curbie@curbie-desktop:~$ mount 
 /dev/sda1 on / type ext4 (rw,errors=remount-ro) 
 proc on /proc type proc (rw,noexec,nosuid,nodev) 
 sysfs on /sys type sysfs (rw,noexec,nosuid,nodev) 
 none on /sys/fs/cgroup type tmpfs (rw) 
 none on /sys/fs/fuse/connections type fusectl (rw) 
 none on /sys/kernel/debug type debugfs (rw) 
 none on /sys/kernel/security type securityfs (rw) 
 udev on /dev type devtmpfs (rw,mode=0755) 
 devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620) 
 tmpfs on /run type tmpfs (rw,noexec,nosuid,size=10%,mode=0755) 
 none on /run/lock type tmpfs (rw,noexec,nosuid,nodev,size=5242880) 
 none on /run/shm type tmpfs (rw,nosuid,nodev) 
 none on /run/user type tmpfs (rw,noexec,nosuid,nodev,size=104857600,mode=0755) 
 none on /sys/fs/pstore type pstore (rw) 
 systemd on /sys/fs/cgroup/systemd type cgroup (rw,noexec,nosuid,nodev,none,name=systemd) 
 gvfsd-fuse on /run/user/1000/gvfs type fuse.gvfsd-fuse (rw,nosuid,nodev,user=curbie) 
 /dev/sdb on /media/curbie/data type ext4 (rw,nosuid,nodev,uhelper=udisks2) 
 /dev/sda3 on /media/curbie/DataCurbie type ext4 (rw,nosuid,nodev,uhelper=udisks2) 
```
 
Where the 500Gb drive labelled “data” is
 /dev/sdb on /media/curbie/data type ext4 (rw,nosuid,nodev,uhelper=udisks2) 
 and the second partition labelled “DataCurbie”of the 1000Gb drive is
 /dev/sda3 on /media/curbie/DataCurbie type ext4 (rw,nosuid,nodev,uhelper=udisks2) [/code]
 
 I presume the mounting of the root,  (the first partition of the 1000Gb) is automatic mounted and not shown by the "mount" command.
 
My fstab is  
 ```
curbie@curbie-desktop:~$ sudo cat /etc/fstab 
 [sudo] password for curbie:  
 # /etc/fstab: static file system information. 
 # 
 # Use 'blkid' to print the universally unique identifier for a 
 # device; this may be used with UUID= as a more robust way to name devices 
 # that works even if disks are added and removed. See fstab(5). 
 # 
 # <file system> <mount point>   <type>  <options>       <dump>  <pass> 
 proc            /proc           proc    nodev,noexec,nosuid 0       0 
 # / was on /dev/sda1 during installation 
 UUID=1ef20c10-da27-47c6-b744-46a1477a1313 /               ext4    errors=remount-ro 0       1 
 # swap was on /dev/sda5 during installation 
 UUID=fc427b57-d9a8-4ed7-955d-b20513d0ddf3 none            swap    sw              0       0 
```
 
 /dev/sda1 is the first partition of my 1000Gb drive and /dev/sda1 is the <swap> partition, so here  begins some of my screw up, from the desktop the icons for filesystem, "data", and "DataCurbie" are all mounted at startup and shown, but not knowing I had to, I never edited into sftab, nor do I know what's automatically mounting the drive labelled "data" or the partition labelled "DataCurbie"?
 
 Should I add the drive labelled "data" and the partition labelled "DataCurbie" to fstab and reboot (after backing up fstab), or do I have yet another issue and should I chase this automatically mounting mystery first?

Curbie

---

### Post by oldfred on 2016-03-09
You normally have to click on a partition to mount it. 
But I did see a post with Unity where partitions were being automounted. I do see that on my live installer, but do not now use Unity so do not know.
You can only mount each partition once, and if you add it to fstab, you must unmount any other mounts.

As mentioned you may have a label "datacurbie" and create a mount "Data" and a mount "DataCurbie" but only one can be in use at a time if for same partiton. Others should give errors.

/dev/sdb on /media/curbie/data type ext4 (rw,nosuid,nodev,uhelper=udisks2) 
 /dev/sda3 on /media/curbie/DataCurbie type ext4 (rw,nosuid,nodev,uhelper=udisks2)

Did you not partition sdb? That normally cannot be mounted as a drive, but should be mounted by each partition.
I believe reference to udisks2 is the auto mount by system.

---

### Post by Curbie on 2016-03-09
OldFred,
 

 &#8220;You normally have to click on a partition to mount it.&#8221;, click on the icon from the desktop to mount it, correct? I always had the partition hard-drive icons just show up on the desktop already mounted without knowing that wasn't correct.
 

 I checked &#8220;man unity&#8221; and it returned &#8220;No manual entry for unity&#8221; and I checked Ubuntu Software Center and no form of &#8220;Unity&#8221; software seems to be installed, so what ever Unity is, I don't think I've used it to automount.
 

 "data" and "DataCurbie" are NOT the same partition, two different partitions on two different drives.
 Yes I partitioned sdb as a single ext4 file system, and that is my understanding that only partitions can be mounted, not drives.
 

 I don't know what set the reference to udisks2 auto mount by system, but I don't recall explicitly doing it, it's always just booted that way.
 

 Curbie

---

### Post by oldfred on 2016-03-09
Unity is the entire Desktop or Gui with default Ubuntu. With larger square icons on left size. 
I use the gnome-panel so not as familiar with Unity as I only use it for a day or two.
       [http://unity.ubuntu.com/about/](http://unity.ubuntu.com/about/) 
    
If using one of the other flavors, Kubuntu, Xubuntu, Lubuntu, then you do not have Unity.

You say you partitioned sdb, but it looks like you formatted sdb not creating partition(s) and formatting those.
Post this:
sudo parted -l
Your blkid already is showning partitions on sda, but just sdb??

---

### Post by Curbie on 2016-03-09
OldFred,
 

 I'm running Xubuntu, so I guess no Unity.
 

 ```
curbie@curbie-desktop:~$ sudo parted -l 
 [sudo] password for curbie:  
 Model: ATA ST500DM002-1BD14 (scsi) 
 Disk /dev/sda: 500GB 
 Sector size (logical/physical): 512B/4096B 
 Partition Table: loop 
  
 Number  Start  End    Size   File system  Flags 
  1      0.00B  500GB  500GB  ext4 
  
  
 Model: ATA WDC WD10EZEX-00B (scsi) 
 Disk /dev/sdb: 1000GB 
 Sector size (logical/physical): 512B/4096B 
 Partition Table: msdos 
  
 Number  Start   End     Size    Type      File system     Flags 
  1      1049kB  492GB   492GB   primary   ext4            boot 
  2      492GB   500GB   8318MB  extended 
  5      492GB   500GB   8318MB  logical   linux-swap(v1) 
  3      500GB   1000GB  500GB   primary   ext4 
```

Curbie

---

### Post by oldfred on 2016-03-09
This says sda is unpartitioned.

Partition Table: loop

---

### Post by Curbie on 2016-03-09
OldFred,
 

 That screw up I must have done three years ago when I did the transition from Win to Xubuntu, again just shows how robust Ubuntu is!

 

 The next plan is is to get the DataCurbie partition mounted on the 1Tb drive and copy the data from the &#8220;data&#8221; drive to that, then I can Gpart a proper partition with a ext4 file system on that 500Gb drive, and copy the data back to same corrected drive.

 

 Then maybe the changes to fstab won't be so twitchy, that's the hope anyway?
 

 Curbie

---

### Post by Curbie on 2016-03-09
OldFred,
  
Does this correct, or did I goof this up again?

  Curbie
  ```

  curbie@curbie-desktop:~$ sudo parted -l
  [sudo] password for curbie:  
  Model: ATA ST500DM002-1BD14 (scsi)
  Disk /dev/sda: 500GB
  Sector size (logical/physical): 512B/4096B
  Partition Table: msdos
  

  Number  Start   End    Size   Type     File system  Flags
   1      1049kB  500GB  500GB  primary  ext4
  

  

  Model: ATA WDC WD10EZEX-00B (scsi)
  Disk /dev/sdb: 1000GB
  Sector size (logical/physical): 512B/4096B
  Partition Table: msdos
  

  Number  Start   End     Size    Type      File system     Flags
   1      1049kB  492GB   492GB   primary   ext4            boot
   2      492GB   500GB   8318MB  extended
   5      492GB   500GB   8318MB  logical   linux-swap(v1)
   3      500GB   1000GB  500GB   primary   ext4
```

---

### Post by oldfred on 2016-03-10
That looks correct and the 35 year old MBR(msdos) partitioning is ok.

But I knew I wanted a new UEFI system back when they first came out, but did not get one until last year.
But Ubuntu could boot from gpt partitioning with either UEFI or BIOS if correct partitions are on drive.
Windows only boots with BIOS from MBR, so last year of XP, I had XP on MBR and Ubuntu on gpt drive.
And all new or totally repartitioned/reformatted drives including most larger flash drives are now gpt.
The change to gpt was more for future proofing drives, so could be used on new system. But not huge advantage.

       GPT Advantages (older but still valid)  see post#2 by srs5694:
[http://ubuntuforums.org/showthread.php?t=1457901](http://ubuntuforums.org/showthread.php?t=1457901)
[https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT](https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT)
[http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface](http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface)
[http://askubuntu.com/questions/629470/gpt-vs-mbr-why-not-mbr](http://askubuntu.com/questions/629470/gpt-vs-mbr-why-not-mbr)
UEFI Advantages
[http://askubuntu.com/questions/647303/uefi-or-legacy-which-is-advised-and-why/647604#647604](http://askubuntu.com/questions/647303/uefi-or-legacy-which-is-advised-and-why/647604#647604)
[http://askubuntu.com/questions/446968/legacy-vs-uefi-help](http://askubuntu.com/questions/446968/legacy-vs-uefi-help)
[http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface](http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface)

---

### Post by Curbie on 2016-03-10
OldFred,
 

 I read a post of yours last weekend, talking in detail about gpt partitioning with either UEFI or BIOS and decided that I would like them for the future compatibility, but until I correct all existing configuration issues first, I'm taking chances with my data, and I don't care if I spend 10x longer, I would prefer not to take any chances. Until I can produce a properly configured system, and then hardware backups for all of it, it's one recoverable step at a time for me.
 

 As an Nimrod example, last night I made a backed up of fstab and edited and tested it, all seemed well to reboot, after all, even if the reboot failed I could boot from cd and just copy back the fstab from backup. Just a recoverable text change, right... WRONG it rebooted ok but swapped the definitions of sda and sdb, I restored the backup fstab and rebooted but still the swapped sda and sdb remained. Not knowing if this was another goof up or normal system change I had to research and think about that,  I concluded was a normal system change or I could recover by starting from scratch from the original drive.
 

 I seem to making progress and as long as there is progress, I'll never remember the effort it took to achieve a stable platform once I have one, and a stable platform is import to me, thanks.
 

 Curbie

---

### Post by oldfred on 2016-03-10
Many years ago, Linux changed from mounting drive by sda, sdb to using UUID. The UUID almost never changes, unless you reformat. But BIOS/UEFI can change boot order. 
On my systems both older BIOS and newer UEFI, I did not plug drives into SATA ports in order. I skipped a port and then when I plugged in a flash drive it became sdf when plugged in, but on reboot became sdb, my sdb became sdc etc.

The instructions on using fstab generally show all 3 ways, using device like sda, using UUID and using label.

And anytime you edit fstab in your system, run this before rebooting. If no errors it will just return to prompt.
sudo mount -a

But that will not tell you if BIOS is not always ordering drives the same.

---

### Post by Curbie on 2016-03-11
OldFred,
 

 Still trying and making some progress (I think?).
 ```

# is comment, do not type
# to verify how the system named the drives  
sudo parted -l                            
# create a mount point directory
sudo mkdir /mnt/DataCurbie                        
# create a mount point, where /dev/sda3 (from parted -l) is my partition and /mnt/DataCurbie is the mount point
sudo mount /dev/sda3 /mnt/DataCurbie
# change the file mode bits for a mount point directory
# Note that the -R is recursion and everything is changed, do NOT run on any system partitions.
# All directories will be 775.
# All files will be 664 except those that were set as executable to begin with.
sudo chmod -R a+rwX,o-w /mnt/DataCurbie
# change ownership from root, to me
sudo chown -R $USER:$USER /mnt/DataCurbie
```

 This all seemed to work with no errors or unexpected flakiness. so...
 
 ```
# edit fstab 
sudo -H mousepad /etc/fstab 
# add new mount point for DataCurbie 
UUID=3951f0f4-c40a-4d00-bab9-e5b54b6ef4be /mnt/DataCurbie ext4 relatime 0 2 
# and save file changes
# test fstab changes
sudo mount -a
```
 
Again, all seemed to work with errors or unexpected flakyness.
 So reboot, and upon reboot, no DataCurbie drive-icon for the partition so...
 
 ```
curbie@curbie-desktop:~$ mount 
 /dev/sda1 on / type ext4 (rw,errors=remount-ro) 
 proc on /proc type proc (rw,noexec,nosuid,nodev) 
 sysfs on /sys type sysfs (rw,noexec,nosuid,nodev) 
 none on /sys/fs/cgroup type tmpfs (rw) 
 none on /sys/fs/fuse/connections type fusectl (rw) 
 none on /sys/kernel/debug type debugfs (rw) 
 none on /sys/kernel/security type securityfs (rw) 
 udev on /dev type devtmpfs (rw,mode=0755) 
 devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620) 
 tmpfs on /run type tmpfs (rw,noexec,nosuid,size=10%,mode=0755) 
 none on /run/lock type tmpfs (rw,noexec,nosuid,nodev,size=5242880) 
 none on /run/shm type tmpfs (rw,nosuid,nodev) 
 none on /run/user type tmpfs (rw,noexec,nosuid,nodev,size=104857600,mode=0755) 
 none on /sys/fs/pstore type pstore (rw) 
 /dev/sda3 on /media/curbie/DataCurbie type ext4 (rw,nosuid,nodev,uhelper=udisks2)  
 systemd on /sys/fs/cgroup/systemd type cgroup (rw,noexec,nosuid,nodev,none,name=systemd) 
 gvfsd-fuse on /run/user/1000/gvfs type fuse.gvfsd-fuse (rw,nosuid,nodev,user=curbie) 
```
 
 and the mount appears to be there, just  no DataCurbie drive-icon?
 
 Any clue on what I goofed up this time?
 
 Curbie

---

### Post by oldfred on 2016-03-11
Sorry, but I use /mnt/data as I do not want an icon. If you want icon then use /media/$USER/DataCurbie.
But you already have this:
/dev/sda3 on /media/curbie/DataCurbie type ext4 (rw,nosuid,nodev,uhelper=udisks2) 
And you cannot mount same partition twice or use same name/mount point twice.

The reason I do not want to see an icon is that I then use links to add all the folders in /mnt/data partition. So Documents
in /home is not really in /home but actually in /mnt/data/Documents. So since all data is linked, I do not need icon.
If you want to see data, you have to go into system or computer and drill down to /mnt  then in /mnt should be you DataCurbie.

---

### Post by Dennis N on 2016-03-11
> and the mount appears to be there, just no DataCurbie drive-icon?

If you mount from fstab but still want an icon to access the mounted file system, may I suggest you just make a bookmark from the file manager for the mount folder or other specific folder?

---

### Post by Curbie on 2016-03-11
Dennis N,
 

 Thanks for the reply, sorry I'm such a Nimrod, was the icon supposed to go away when someone changes the mount point from media to mnt, or did I goof something up?

 

 My issue is, I don't know what to expect, so when something happens that is unexpected, I don't know if it's a normal system change, or a goof up.
 

 Thanks,
 Curbie

---

### Post by Dennis N on 2016-03-11
> **Curbie said:**
> Dennis N,
Thanks for the reply, sorry I'm such a Nimrod, was the icon supposed to go away when someone changes the mount point from media to mnt, or did I goof something up?
My issue is, I don't know what to expect, so when something happens that is unexpected, I don't know if it's a normal system change, or a goof up. Thanks, Curbie

You didn't do anything wrong. The rule is that whenever you mount a device (a partition, for example) with an entry in fstab, you won't see any icon on your desktop or in Thunar. So a bookmark is the way we can easily open and browse that device in a file manager window. Also, when you mount a partition from Thunar, it always mounts at /media/your-user-name/some-folder-name.

---

### Post by Curbie on 2016-03-11
Dennis N, thanks for your help.
 

 I need to consolidate 6 pages of notes for the future on what I've been taught on all this, come up with a new labeling plan for all the hard drives, and start thinking about a transition to gpt and UEFI for future compatibility. But THIS issue is SOLVED, and will mark it as such!
 

 Many, many thanks to OldFred, in my opinion, without people like you spending valuable time helping Ubuntu users like me, in a forum like this, all the time and effort people spend creating Ubuntu would be near worthless to newbies.
 

 Curbie

---

### Post by oldfred on 2016-03-11
Glad we all could help.
And the forum is always here for more help when needed.

---

