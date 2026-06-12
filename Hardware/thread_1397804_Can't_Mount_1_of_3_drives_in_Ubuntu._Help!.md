---
title: "Can't Mount 1 of 3 drives in Ubuntu. Help!"
date: 2010-02-03
forum: Hardware
---

### Post by AtrocityDT on 2010-02-03
Hello all, I'm a brand new user to Ubuntu, but loving every minute of it!

I am single booting ubuntu 9.10 (vista is installed but not working right now)

I have 4 physical drives:
2x 73gig in raid -- correctly mounted (windows install on this raid)
1x 250g -- shows as 'file system' (ubuntu installed on this drive)
1x 500g -- cannot mount it.

I've been browsing forums trying to mount my 500g hard drive... which has ALL my music and photos etc, I need to access it!

Here is the FDISK -l data to help anyone with time to help:
------------------------------------------------------
atrocitydt@Kory:~$ sudo fdisk -l

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x075d075d

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       29164   234259798+  83  Linux
/dev/sda2           29165       30401     9936202+   5  Extended
/dev/sda5           29165       30401     9936171   82  Linux swap / Solaris

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x5dc6faba

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       29164   234259798+  83  Linux
/dev/sdb2           29165       30401     9936202+   5  Extended
/dev/sdb5           29165       30401     9936171   82  Linux swap / Solaris

Disk /dev/sdc: 74.4 GB, 74355769344 bytes
255 heads, 63 sectors/track, 9039 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x816cf889

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       18080   145223680    7  HPFS/NTFS

Disk /dev/sdd: 74.4 GB, 74355769344 bytes
255 heads, 63 sectors/track, 9039 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000

Disk /dev/sdd doesn't contain a valid partition table
--------------------------------------


Can anyone help me get my 500gig hard drive mounted in linux w/o me having to format it??

Thank you,

Kory

---

### Post by AtrocityDT on 2010-02-03
So far I've tried this code:

atrocitydt@Kory:~$ sudo mount -t ntfs-3g /dev/sdb5 /media/drive -o ro,force,gid=100

and other variations... I think my problem is that /dev/sdb5 doesn't have an ntfs partition? What should I do?

---

### Post by mgichoga on 2010-02-03
Going by the output you submitted...

> Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x5dc6faba

Device Boot Start End Blocks Id System
/dev/sdb1 1 29164 234259798+ 83 Linux
/dev/sdb2 29165 30401 9936202+ 5 Extended
/dev/sdb5 29165 30401 9936171 82 Linux swap / Solaris

This disk seems to contain a Linux partition. /dev/sdb5 is Linux swap therefore you cannot mount it as NTFS. Did you install Linux to this drive by mistake?

---

### Post by AtrocityDT on 2010-02-03
I sure hope not. I only chose the 250g hard drive for installation. How do I tell if my 500g hard drive is formatted? It shouldn't be, but how could I check it through linux? all I see if a "Filesystem" drive, and the 149gb filesystem I have to manually mount every time.

I'm assuming 'Filesystem' is the install drive (250g) and the 500g is just missing.

---

### Post by mgichoga on 2010-02-03
Let me see if I have this right. Was the 500GB drive formatted using NTFS? - was it visible when you were in windows? The music + photos you are talking about was saved while you were in linux or windows?

> All I see if a "Filesystem" drive, and the 149gb filesystem..

The reason you see the 149GB drive is perhaps it is on raid1 courtesy of windows(striped).

You need to find out which drive your filesystem is on. Please post the output of the mount command.

> sudo mount

---

### Post by AtrocityDT on 2010-02-03
Ok, so I think I know the problem now. I right clicked 'filesystem' and clicked properties. It is still tallying my total space, but so far its located 440,000 files totaling over 146.7 gig. My free space listed below is 192.7 gig. So, that adds up to over the 250gig of the install drive (146.7+192.7>250g). So I'm assuming the 500gig hd is already added somehow... but it does say (some contents unreadable). 

How would I fix this unreadable contents? I suspect my music is in this unreadable area....

Do I need to boot to windows and backup all my files, and format the 500g hd? I really want to avoid doing that if at all possible.

---

### Post by AtrocityDT on 2010-02-03
> **mgichoga said:**
> Let me see if I have this right. Was the 500GB drive formatted using NTFS? - was it visible when you were in windows? The music + photos you are talking about was saved while you were in linux or windows?


Music + Photos were all saved in windows. I didn't format the 500gb drive in linux or windows. I installed linux 2 nights ago, and during the setup I chose to format the 250g drive. 

Here is the output you requested
-------------------------------
atrocitydt@Kory:~$ sudo mount
[sudo] password for atrocitydt: 
/dev/mapper/nvidia_eajhggdi1 on / type ext4 (rw,errors=remount-ro)
proc on /proc type proc (rw)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
udev on /dev type tmpfs (rw,mode=0755)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
none on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
/home/atrocitydt/.Private on /home/atrocitydt type ecryptfs (ecryptfs_sig=d546856bc2d836ac,ecryptfs_fnek_sig=a1be1b4009931aa0,ecryptfs_cipher=aes,ecryptfs_key_bytes=16)
gvfs-fuse-daemon on /home/atrocitydt/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=atrocitydt)
/dev/mapper/nvidia_jbdfbfdi1 on /media/F8124C94124C5A30 type fuseblk (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)

---

### Post by mgichoga on 2010-02-03
I'm a little puzzled here. I hope someone else can help out too. Do not rush into formatting drives until you are sure you have your data. 

You could try browsing to the following folder and see if your files are there

/media/F8124C94124C5A30

Also post the ouptput of the Disk Free program

> sudo df -h

---

### Post by AtrocityDT on 2010-02-03
> **mgichoga said:**
> I'm a little puzzled here. I hope someone else can help out too. Do not rush into formatting drives until you are sure you have your data. 

You could try browsing to the following folder and see if your files are there

/media/F8124C94124C5A30

Also post the ouptput of the Disk Free program

^^ that /media/f8124c94124c5a30 is my raid drive, that I have to manually mount every time.

Output below:
-----------------
atrocitydt@Kory:~$ sudo df -h
[sudo] password for atrocitydt: 
Filesystem            Size  Used Avail Use% Mounted on
/dev/mapper/nvidia_eajhggdi1
                      220G   17G  193G   8% /
udev                  2.0G  348K  2.0G   1% /dev
none                  2.0G  756K  2.0G   1% /dev/shm
none                  2.0G  204K  2.0G   1% /var/run
none                  2.0G     0  2.0G   0% /var/lock
none                  2.0G     0  2.0G   0% /lib/init/rw
/home/atrocitydt/.Private
                      220G   17G  193G   8% /home/atrocitydt
/dev/mapper/nvidia_jbdfbfdi1
                      139G  134G  5.5G  97% /media/F8124C94124C5A30

---

### Post by AtrocityDT on 2010-02-03
Here is how I know Linux is looking at the 500g hd, but I cannot see the file tree to try and navigate to any files: (see image)

---

### Post by mgichoga on 2010-02-03
Unless my guess is wrong, I think you have formatted the 500GB with Linux. It seems you are booting out of the 250 GB though. You can use Gparted to confirm this. I don't know if it is installed by default in the new version but you can get it from the software center under system tools. DO NOT format any drives. This is just to confirm if indeed this drive has been partitioned and formatted for Linux use.

System > Administration > Gparted

On the drop down on the right, choose /dev/sdb

You can post the screenshot.

---

### Post by AtrocityDT on 2010-02-03
> **mgichoga said:**
> Unless my guess is wrong, I think you have formatted the 500GB with Linux. It seems you are booting out of the 250 GB though. You can use Gparted to confirm this. I don't know if it is installed by default in the new version but you can get it from the software center under system tools. DO NOT format any drives. This is just to confirm if indeed this drive has been partitioned and formatted for Linux use.

System > Administration > Gparted

On the drop down on the right, choose /dev/sdb

You can post the screenshot.

SS posted.

---

### Post by mgichoga on 2010-02-03
Not good! Looks like you formatted half of the 500GB drive, the other half is unallocated. Hopefully some other senior forum members can advise how to move on from here. Recovering data after a format is beyond my scope of knowledge.

---

### Post by AtrocityDT on 2010-02-03
> **mgichoga said:**
> Not good! Looks like you formatted half of the 500GB drive, the other half is unallocated. Hopefully some other senior forum members can advise how to move on from here. Recovering data after a format is beyond my scope of knowledge.

Well I hope thats not the case. I do know about half the drive was free of data when I last accessed it in windows... thanks of your help bud, I think what I need to do is get windows booting, and then check it from there. I have a feeling that might be the quickest and surest way to proceed.

---

### Post by AtrocityDT on 2010-02-03
Something odd I noticed... my sda1 is the same exact size as my sdb1 (for file size on the disk) I think there is some sort of mistake here with the coding. Is it making the 2 disks act like a raid mirror?

---

### Post by AtrocityDT on 2010-02-04
Bump? Still need help with my 500g drive... if any xperts out there

---

