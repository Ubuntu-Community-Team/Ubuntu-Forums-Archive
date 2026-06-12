---
title: "Western Digital HDD failure"
date: 2014-04-29
forum: Hardware
---

### Post by Ewald_Jurgens on 2014-04-29
I have an Ubuntu desktop 12.04 LTS running which I am using as a server (just with desktop support). Now for 1,5 years it is running like a train, nothing wrong. I am using it for many things, fileserver (samba), streaming server, ssh server, vpn server, teamspeak 3 server etc.. etc..  I have 3 disks on it. one which is devided in several partiotions which includes root home swap etc.. and the other 2 are only used for file storage. those 2 are a 2TB and a 3TB WD green disk. 3 days ago it was all working fine, the 2 TB contains 2TB of mostly series i was watching on my smart tv in either the livingroom or bedroom or on my Phone, worked like a charm. In the morning when i woke up i have been watching one without any problems. In the evening when i came home i discovered that 3/4th of the series were gone. Eventhough my g/d watches them to she has no access to the system it is running on, so she could not have deleted them. When i was running testdisk to try and get it all back, testdisk was not able to find any.
Then I though, well no problem I'll be able to get it all back, let's just reformat everything, but that is where the problem started... I tried to reformat it using departed and it kept saying that the drive is in use by the system and it could not do it. So I unmounted it and removed it from /etc/fstab and then did a reboot of the system. Unfortunately after the boot the same error occured and i checked if it was mounted, but it returned that it was not mounted. I checked /etc/fstab again, but it was not in the list anymore.
I tried it with the command
```
sudo mkfs -t ext4 /dev/sdb1
```
but it returned 
```
/dev/sdb1 is apparently in use by the system; will not make a filesystem here!
```
then i thought i could do it with a live USB because the system will then not have it in use(same Ubuntu version) and that worked, it mounted a 2TB HDD and it said 1.88TBB is available (which was the amount before it crashed)
Then I went back to the normal installation with the new formated disk and 1 EXT4 partition. but sadly under the Installed Ubuntu in gparted it said
233,18 GB unknown filesystem 1,59TiB unallocated.
This is where i got lost and tried to google the answer and all people with the same problem seem to have deliberately put the HDD in raid. First of all I am sure i have never put it in raid myself, second they said to test it with the command tool mdadm, but that command tool is not even installed in my Ubuntu. 

```
sudo fdisk -l
``` returns

```
Disk /dev/sdb: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x0002fa87
   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1             256   488378623   244189184   83  Linux

```

the command s```
udo mount
``` returned the following

```
[EMAIL="ewald@server:~$"]ewald@server:~$[/EMAIL] sudo mount
/dev/sda1 on / type ext4 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
udev on /dev type devtmpfs (rw,mode=0755)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
tmpfs on /run type tmpfs (rw,noexec,nosuid,size=10%,mode=0755)
none on /run/lock type tmpfs (rw,noexec,nosuid,nodev,size=5242880)
none on /run/shm type tmpfs (rw,nosuid,nodev)
/dev/sda6 on /media/MUZIEK type ext4 (rw)
/dev/mapper/350014ee2b3612295-part1 on /media/FILMSHD type ext4 (rw)
/dev/sda2 on /home type ext4 (rw)
gvfs-fuse-daemon on /var/lib/lightdm/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=lightdm)
gvfs-fuse-daemon on /home/ewald/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=ewald)
```


I then plugged the HDD into my windows 7 computer, and did a format with a NTFS file system and it worked like a charm, just as it did under the live USB, so it does not appear to me as a faulty HDD but more as a faulty config in the installed Ubuntu.
I then tried to use the Western Digital program to check the status off the HDD (slow check) 16 hours later it returned the disk as fully working and functional, no disk errors at all
I even partitioned it was minitool partition wizard in windows with an EXT4 partition and plugged it back in the Ubuntu system, but the results are exactly the same, 
233,18 GB unknown filesystem 1,59TiB unallocated.

Anyone here that can help me out here. I would really like to get the HDD working again

With kind regards

Ewald

---

### Post by Mark Phelps on 2014-04-29
I had a WD Green 2TB drive totally fail on me after only a few months of use. I first noticed it when file access slowed way down and ran the WD diags on it.  Within a few days, it was totally useless and the WD diags returned "too many errors ...".

Since this was the third WD "green" drive that failed within a year's time, I quit using them and switched over to Seagate -- which I'm sure folks will badmouth, if given the chance -- but I've had no more drive failures in nearly two years now.

My own advice is to export the stuff from the WD drive as much as you can and switch to a different brand or model.

---

