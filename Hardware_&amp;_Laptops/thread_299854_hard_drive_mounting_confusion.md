---
title: "hard drive mounting confusion"
date: 2006-11-14
forum: Hardware &amp; Laptops
---

### Post by dizzylizard on 2006-11-14
Ok, so this problem has probably been addressed already, but I have a wife who doesn't understand that it takes time to search for answers...lol.  Anyway, here goes:  I have a system set up with a 10g boot/OS drive and a 40g media storage drive...I had to replace the OS drive, and the new installation of Ubuntu (Dapper) isn't recognizing any of the data which is stored on the media storage drive.  Fdisk -l gives me the following response:

Disk /dev/hda: 10.2 GB, 10262568960 bytes
255 heads, 63 sectors/track, 1247 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        1192     9574708+  83  Linux
/dev/hda2            1193        1247      441787+   5  Extended
/dev/hda5            1193        1247      441756   82  Linux swap / Solaris

Disk /dev/hdc: 41.1 GB, 41110142976 bytes
255 heads, 63 sectors/track, 4998 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdc1               1        2295    18434556   83  Linux
/dev/hdc2            2296        4998    21711847+  83  Linux

and more /etc/fstab gives the following:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdd        /media/cdrom0   udf,iso9660 user,noauto     0       0

So my question is: What do I do next???
Thanks for your help to a newbie!](*,)

---

### Post by futz on 2006-11-15
Ok, this is pretty easy. Your storage drive is not getting mounted, so you'll have to set that up.

First, make a couple directories in /media called hdc1 and hdc2
```
sudo mkdir /media/hdc1
sudo mkdir /media/hdc2
```
Set file ownership to you, the user, instead of root and set permissions to 755. I usually start a root nautilus with "gksudo nautilus" to do this job, since I can never remember how to do it in the command line. If you want more detail on this, ask.

Then edit your fstab file 
```
sudo gedit /etc/fstab
```
and add these lines 
```
/dev/hdc1       /media/hdc1     ext3    defaults        0       2
/dev/hdc2       /media/hdc2     ext3    defaults        0       2
```

Save it and test your fstab now by doing 
```
sudo mount /dev/hdc1
```
If that works with no errors, then mount the other one (sudo mount /dev/hdc2). Next time you boot the machine up they'll automount, so you won't have to manually mount them every time.

I think that's everything. If I screwed up, ask and I'll correct myself.

---

### Post by jhenager on 2006-11-15
You might also try this script posted in BLTicklemonster's sig:
[https://help.ubuntu.com/community/AutomaticallyMountPartitions#head-f59428cd4d1c1b020a3a06bae2242b3d7f45a06d](https://help.ubuntu.com/community/AutomaticallyMountPartitions#head-f59428cd4d1c1b020a3a06bae2242b3d7f45a06d)
It worked great for me.

---

### Post by dizzylizard on 2006-11-16
ok...got the drive mounted, but my datafiles still aren't there...

sudo fdisk -l

Disk /dev/hda: 10.2 GB, 10262568960 bytes
255 heads, 63 sectors/track, 1247 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        1192     9574708+  83  Linux
/dev/hda2            1193        1247      441787+   5  Extended
/dev/hda5            1193        1247      441756   82  Linux swap / Solaris

Disk /dev/hdc: 41.1 GB, 41110142976 bytes
255 heads, 63 sectors/track, 4998 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdc1               1        2295    18434556   83  Linux
/dev/hdc2            2296        4998    21711847+  83  Linux
:~$ sudo more /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdd        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdc1       /media/hdc1     ext3    defaults        0       2
/dev/hdc2       /media/hdc2     ext3    defaults        0       2

but when I go into /media/hdc1(or 2), there's nothing...but the free space only adds up to 35.5 gig...what am I doing wrong?:confused:

---

### Post by futz on 2006-11-16
> ok...got the drive mounted, but my datafiles still aren't there...

Disk /dev/hdc: 41.1 GB, 41110142976 bytes

but when I go into /media/hdc1(or 2), there's nothing...but the free space only adds up to 35.5 gig...what am I doing wrong?
35.5GB sounds probably about right for a 40GB drive. The advertised size is *before* formatting. Formatting takes some overhead.

You're sure the drives are properly mounted? If they aren't, that would explain the empty hdc1 and hdc2 directories. If they *are* mounted, they'll show up as icons on a stock Ubuntu's desktop and listed as separate drives in Nautilus. 

If they are not mounted, they won't show up like that. You could still navigate to /media/hdc1 or hdc2, but the directories will be empty.

Or it's possible that you accidently told the partitioner to format the drives when you reinstalled. That would be... very bad. :(

---

### Post by dizzylizard on 2006-11-17
I could have, but I don't think I did...isn't there an install log that would record something as potentially catastrophic as that?  The data on that drive was pretty important...and unfortunately not backed up...](*,) ](*,)

---

### Post by jjandian on 2006-11-18
I also have a hard drive problem in that I am trying to find out if my primary 160GB hard drive on my HP Pavilion a450n has failed for good, or just stopped wanting to boot as a Windows device.  I booted from my Ubuntu disc and can't find the volume for my hard drive.  Response to
ubuntu@ubuntu:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
unionfs               874M  702M  172M  81% /
varrun                252M   80K  252M   1% /var/run
varlock               252M  4.0K  252M   1% /var/lock
udev                  252M  128K  252M   1% /dev
devshm                252M     0  252M   0% /dev/shm
lrm                   252M  8.8M  244M   4% /lib/modules/2.6.15-23-386/volatile
tmpfs                 252M   12K  252M   1% /tmp
/dev/fd0              1.4M  117K  1.3M   9% /media/floppy

---

### Post by futz on 2006-11-20
> **dizzylizard said:**
> I could have, but I don't think I did...isn't there an install log that would record something as potentially catastrophic as that?  The data on that drive was pretty important...and unfortunately not backed up...](*,) ](*,)
When you tested your new fstab with
```
sudo mount /dev/hdc1
```
did you get an error like this?
```
mount: wrong fs type, bad option, bad superblock on /dev/sda2,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so
```

If you did (and possibly even if you didn't), then that means your drive is not formatted as ext3, and you'll have to find out what format those partitions are. They could be reiserfs or any of something like a couple dozen other types, tho only 3 or 4 different types are likely. I know there is an easy tool to find out the disk type, but I don't know what it is offhand. Once you know, you replace the ext3 in these fstab lines
```
/dev/hdc1       /media/hdc1     ext3    defaults        0       2
/dev/hdc2       /media/hdc2     ext3    defaults        0       2
```
with the correct type and try mounting again.

The reasons I told you ext3 at first are:
1. I thought type 83 meant ext3. I was wrong. While tinkering with mine tonight I realized that 83 can mean either ext3 or reiserfs, and probably a few others.
2. I assumed you would probably have used defaults for the partitions when you first created them, and that they would therefore very likely be ext3.

---

### Post by dizzylizard on 2006-11-22
> **futz said:**
> When you tested your new fstab with
```
sudo mount /dev/hdc1
```
did you get an error like this?
```
mount: wrong fs type, bad option, bad superblock on /dev/sda2,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so
```

If you did (and possibly even if you didn't), then that means your drive is not formatted as ext3, and you'll have to find out what format those partitions are. They could be reiserfs or any of something like a couple dozen other types, tho only 3 or 4 different types are likely. I know there is an easy tool to find out the disk type, but I don't know what it is offhand. Once you know, you replace the ext3 in these fstab lines
```
/dev/hdc1       /media/hdc1     ext3    defaults        0       2
/dev/hdc2       /media/hdc2     ext3    defaults        0       2
```
with the correct type and try mounting again.

The reasons I told you ext3 at first are:
1. I thought type 83 meant ext3. I was wrong. While tinkering with mine tonight I realized that 83 can mean either ext3 or reiserfs, and probably a few others.
2. I assumed you would probably have used defaults for the partitions when you first created them, and that they would therefore very likely be ext3.
I know they're formatted ext3...I didn't get any error codes, just couldn't find my datafiles...

---

