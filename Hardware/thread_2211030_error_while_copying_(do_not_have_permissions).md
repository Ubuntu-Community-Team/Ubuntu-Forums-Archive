---
title: "error while copying (do not have permissions)"
date: 2014-03-13
forum: Hardware
---

### Post by Chuck_Finley on 2014-03-13
Hey I am new,

So I will try and fill you guys in on all the details.

Using Gparted I can see all the partitions. Ubuntu is installed on my ssd /dev/sdb. I also see sdb1 (fat32), sdb2 ext4(what ever that is), and sdb3 (linux-swap). I am thinking I may have installed ubuntu more than once by accident. 

Well this isnt really my problem right now which is that I tried to add a disk drive after I installed ubuntu on my ssd. Then using gparted I deleted the the partition on this extra drive and created a new. Now I all I see is a folder that says lost+found and I cannot move anything into directory which is media/disk2. I right click and mount then unmount but nothing.

I will keep searching for a answer but any help would be much appreciated :D

---

### Post by steeldriver on 2014-03-13
Hello and welcome to the forums

What exactly is your end goal? it's hard to give specific advice until we know what you're trying to do

Also it sounds like you are confused between the device (/dev/sdb) and the partitions on that device (/dev/sdb**1**, /dev/sdb**2** etc)

---

### Post by Chuck_Finley on 2014-03-13
My goal is to have extra space that I can add games or other media to. But I cant seem to copy anything or even create new folders in this drive. From what I have read it seems that I do not have the file system permissions. Just cant figure out how to fix this issue.

---

### Post by steeldriver on 2014-03-13
What kind of drive is it? What version and flavor of Ubuntu (plain Ubuntu / Lubuntu / Xubuntu etc.)?

USB pluggable drives are generally handled in 'user-space' and get auto-mounted with appropriate ownership so that the currently logged in primary user can write to them. By manually mounting it via gparted you have made life more complicated than necessary.

It might help if you open a terminal (Ctrl-Alt-t) and post back the output of the command

```
mount
```

---

### Post by Chuck_Finley on 2014-03-13
its a Samsung sata 1TB hard drive. 

Distributor ID:    Ubuntu
Description:    Ubuntu 12.04.4 LTS
Release:    12.04
Codename:    precise



Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x1709d321

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1            2048  1953523711   976760832   83  Linux

WARNING: GPT (GUID Partition Table) detected on '/dev/sdb'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sdb: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1   234441647   117220823+  ee  GPT
chuck@chuck-desktop:~$ clear

chuck@chuck-desktop:~$ lsb_release -a
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 12.04.4 LTS
Release:    12.04
Codename:    precise
chuck@chuck-desktop:~$ mount
/dev/sdb2 on / type ext4 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
none on /sys/firmware/efi/efivars type efivarfs (rw)
udev on /dev type devtmpfs (rw,mode=0755)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
tmpfs on /run type tmpfs (rw,noexec,nosuid,size=10%,mode=0755)
none on /run/lock type tmpfs (rw,noexec,nosuid,nodev,size=5242880)
none on /run/shm type tmpfs (rw,nosuid,nodev)
/dev/sdb1 on /boot/efi type vfat (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/chuck/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=chuck)
/dev/sr0 on /media/Aug 17 2013 type udf (ro,nosuid,nodev,uid=1000,gid=1000,iocharset=utf8,umask=0077,dmode=0500,uhelper=udisks)
/dev/sda1 on /media/Disk 2 type ext2 (rw,nosuid,nodev,uhelper=udisks)
truecrypt on /tmp/.truecrypt_aux_mnt1 type fuse.truecrypt (rw,nosuid,nodev,allow_other)
/dev/mapper/truecrypt1 on /media/truecrypt1 type vfat (ro,uid=1000,gid=1000,umask=077)
chuck@chuck-desktop:~$ clear

---

### Post by Chuck_Finley on 2014-03-14
Alright I tried and to check the drive for errors as instructed here [https://help.ubuntu.com/community/TestingStorageMedia](https://help.ubuntu.com/community/TestingStorageMedia).

I have to unmount the drive to do so but doing so gives me the following error message:

"unable to unmount disk"
"daemon is inhibited"

So I am thinking the hard drive as gone bad? I suppose thats possible considering this extra hard drive was just laying around in my basement. Is there anyway for me to confirm this?

---

### Post by steeldriver on 2014-03-14
Based on your mount output

```

/dev/sda1 on /media/Disk 2 type ext2 (rw,nosuid,nodev,uhelper=udisks)

```

it looks like the disk was auto-mounted by udisks rather than manually mounted using gparted or the 'mount' command - try 

```

udisks --unmount /dev/sda1

```

in the terminal

---

### Post by Chuck_Finley on 2014-03-14
chuck@chuck-desktop:~$ udisks --unmount /dev/sda1
Unmount failed: Daemon is inhibited

but then after a search I found this:

sudo killall udisks 

this worked :D

Now I will try and check the disk for errors. thanks

---

### Post by Chuck_Finley on 2014-03-14
alright so I used 
sudo touch /forcefsck

and then after a restart I saw a brief scan of the drive. I am guessing everything is fine then? I am lost here as to why I cannot get the proper privelages in order to use this disk space.

---

### Post by steeldriver on 2014-03-14
What is the output of 

```

ls -l /media

```

---

### Post by Chuck_Finley on 2014-03-14
alright so I used sudo lshw -c disk and I see the following. partitioned dos? Whats that...

  *-disk                  
       description: ATA Disk
       product: SAMSUNG HD103SJ
       physical id: 0.0.0
       bus info: scsi@0:0.0.0
       logical name: /dev/sda
       version: 1AJ1
       serial: S246J1RZ700659
       size: 931GiB (1TB)
      ** capabilities: partitioned partitioned:dos** ?
       configuration: ansiversion=5 signature=1709d321

---

### Post by Chuck_Finley on 2014-03-14
chuck@chuck-desktop:~$ ls -l /media
total 18
dr-x------ 2 chuck chuck   100 Sep 10  2013 Aug 17 2013
drwx------ 3 chuck chuck 16384 Dec 31  1969 truecrypt1

---

### Post by Chuck_Finley on 2014-03-14
chuck@chuck-desktop:~$ ls -l /media
total 18
dr-x------ 2 chuck chuck   100 Sep 10  2013 Aug 17 2013 (this is a cd in my disc drive)
drwx------ 3 chuck chuck 16384 Dec 31  1969 truecrypt1 (and this is true crypt which  is used to mount a encrypted volume from the cd above)

I dont see the samsung hard drive at all or my ssd.

so then I tried sudo lshw -c disk

and i have the following


  *-disk                  
       description: ATA Disk
       product: SAMSUNG HD103SJ
       physical id: 0.0.0
       bus info: scsi@0:0.0.0
       logical name: /dev/sda
       version: 1AJ1
       serial: S246J1RZ700659
       size: 931GiB (1TB)
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5 signature=1709d321
  *-disk
       description: ATA Disk
       product: OCZ-VERTEX3
       physical id: 0.0.0
       bus info: scsi@2:0.0.0
       logical name: /dev/sdb
       version: 2.25
       serial: OCZ-031O0D57O1S51UUB
       size: 111GiB (120GB)
       capabilities: gpt-1.00 partitioned partitioned:gpt
       configuration: ansiversion=5 guid=22f298fb-643a-4e79-b10e-d53748a7e2db
  *-cdrom
       description: DVD-RAM writer
       product: iHAS120   6
       vendor: ATAPI
       physical id: 0.0.0
       bus info: scsi@4:0.0.0
       logical name: /dev/cdrom
       logical name: /dev/cdrw
       logical name: /dev/dvd
       logical name: /dev/dvdrw
       logical name: /dev/sr0
       logical name: /media/Aug 17 2013
       version: 7L0E
       capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
       configuration: ansiversion=5 mount.fstype=udf mount.options=ro,nosuid,nodev,relatime,uid=1000,gid=1000,umask=77,dmode=500,iocharset=utf8 state=mounted status=ready
     *-medium
          physical id: 0
          logical name: /dev/cdrom
          logical name: /media/Aug 17 2013
          configuration: mount.fstype=udf mount.options=ro,nosuid,nodev,relatime,uid=1000,gid=1000,umask=77,dmode=500,iocharset=utf8 state=mounted

p s 

sorry for the double posting my page wasnt loading correctly.

---

### Post by Chuck_Finley on 2014-03-14
hmm i have the drive mounted in /mnt but I still cannot access this drive.. is there something that I am missing?

---

### Post by Chuck_Finley on 2014-03-14
i see that folders like home and /mnt in permissions are owned by root, not me (chuck). Is this intentional and I have to learn some things or is something wrong?

---

### Post by Chuck_Finley on 2014-03-15
Alright,

I changed hard drives just in case it was dead. I also reinstalled ubuntu. I have my second extra hard drive partitioned and mounted in /home/. I guess I just dont understand how this filesystem works. On windows my main drive would be C. My extra drive would be D and totally seperate. But since everything appears to be one big filesystem in linux how do I know when something is installed on my extra drive or not? I dont see anything in /home indicating my extra hard drive is there. I hope that make sense.. I read the tutorials but I still dont understand the idea of having this extra hard drive.

---

### Post by steeldriver on 2014-03-15
Hi again

I'm confused now - first you said it was mounted in /media, then it was in /mnt, now it's in /home - **how **exactly are you mounting this? Do you have an entry for it in /etc/fstab?

If this is an internal HDD and you want to permanently mount it for additional storage that's a different process from a pluggable USB drive that you want to use for ad hoc storage. For example on my HTPC I have a couple of big disks mounted at /var/lib/mythtv which just 'transparently' extend the video storage capabilities. What do you want to use the disk for?

---

### Post by Chuck_Finley on 2014-03-15
Alright I have been mounting to several locations while making new partitions over and over. I concluded that hard drive was broken. I took another spare hard drive that I had and it extended my drive space and works just fine. Now it sounds like I may have mounted the hard drive wrong since I did not want to just extend my hard drive space but use that space exclusively for games and such. I mean I actually wanted to see the two drives seperate but not just a total amount of space combined together. My reasoning for this was that I did not want to kill my ssd drive (apparently ssd drives can only have so much copied over and over before they break).

So in conclusion I wanted to have seperate hard drives available not one big combined drive (which is what I have right now). I am happy with the extended drive though I will just take that as working lol..

chuck@chuck-desktop:~$ sudo fdisk -l

WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1   625142447   312571223+  ee  GPT

WARNING: GPT (GUID Partition Table) detected on '/dev/sdb'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sdb: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1   234441647   117220823+  ee  GPT
You must set cylinders.
You can do this from the extra functions menu.

Disk /dev/mapper/truecrypt1: 0 MB, 786432 bytes
255 heads, 63 sectors/track, 0 cylinders, total 1536 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

---

### Post by Chuck_Finley on 2014-03-16
Alright I appreciate the help steel driver. I still dont understand what was wrong but after several reinstalls and swapping hard drives I just don't have this issue anymore. It could possibly be the learning curve I am going through.

---

