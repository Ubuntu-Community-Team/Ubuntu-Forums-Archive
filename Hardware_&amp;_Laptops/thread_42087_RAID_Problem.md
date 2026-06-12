---
title: "RAID Problem"
date: 2005-06-16
forum: Hardware &amp; Laptops
---

### Post by RIOT on 2005-06-16
Performed a fresh install of Hoary with the main install going onto a 20GB IDE hard drive and a RAID5 setup of three 9.1GB SCSI hard drives for a shared directory.  During the booting process, I saw an error:

```

* Starting RAID devices...
* adm:  error opening /dev/md0:  No such file or directory
...
*Checking all filesystems...
fsck.ext3:  no such file or directory while trying to open /dev/md0 /dev/md0:
The superblock could not be read or does not descride a correct ext2 filesystem.  If the device is valid and it really contains an ext2 filesystem (and not swap or ufs or something else), then the superblock is corrupt, and you might try running e2fsck with an alternate superblock:
     e2fsck -b 8193 <device>
*
*fsck failed.  Please repair manually

``` 

I pressed CTRL-D to continue booting and didn't think anything of it because I had seen this error before on a previous Hoary install and the SCSI drives worked fine.  Of course, now I realize that I didn't have a RAID array then either.

After playing around a bit I noticed eveything that should have been placed in the shared directories on the SCSI drives was being placed on the IDE drive.  Now I'm figuring out that the SCSI drives and the RAID array I created during install are not being used at all.

I've searched around the forums and noticed other people having problems with RAID setups, and I tried some of the suggested things.  Such as using mdadm to create another arrary, but I get the error message:

```

mdadm:  error opening /dev/md0:  No such file or directory

```

I ran sudo fdisk -l and got the following:

```

Disk /dev/hda: 20.0 GB, 20020396032 bytes
255 heads, 63 sectors/track, 2434 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        2341    18804051   83  Linux
/dev/hda2            2342        2434      747022+   5  Extended
/dev/hda5            2342        2434      746991   82  Linux swap / Solaris

Disk /dev/sda: 9100 MB, 9100369920 bytes
255 heads, 63 sectors/track, 1106 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        1106     8883913+  fd  Linux raid autodetect

Disk /dev/sdb: 9100 MB, 9100369920 bytes
255 heads, 63 sectors/track, 1106 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        1106     8883913+  fd  Linux raid autodetect

Disk /dev/sdc: 9100 MB, 9100369920 bytes
255 heads, 63 sectors/track, 1106 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1        1106     8883913+  fd  Linux raid autodetect

```

Any help getting my RAID working would be greatly appreciated...

---

### Post by steven_ellis on 2005-06-16
You might want to take a look at [this link](http://www.ubuntuforums.org/showthread.php?t=27723&highlight=mdadm+raid) but I can't be sure you have the same problem.


I'm having similar raid issues.

I have the following RAID 1 partitions

```
/dev/md2 = /boot
/dev/md3 = /
/dev/md4 = /home
```

And the following Raid 0 partitions

```
/dev/md0 = /video/capture
/dev/md1 = /video/capture2
```
If I look at /etc/mdadm/mdadm.conf I have

```
DEVICE partitions
ARRAY /dev/md4 level=raid1 num-devices=2 UUID=63b054c9:d6b959a4:7273d641:a28743ea
   devices=/dev/hdb6,/dev/hda6
ARRAY /dev/md3 level=raid1 num-devices=2 UUID=689f7488:a6bc5e47:42924063:c829c439
   devices=/dev/hdb5,/dev/hda5
ARRAY /dev/md2 level=raid1 num-devices=2 UUID=033ffaf5:fd7f595b:6996dd14:74c90456
   devices=/dev/hdb2,/dev/hda3
ARRAY /dev/md1 level=raid0 num-devices=2 UUID=fc4f146f:d72a5f00:4333e628:9247f19e
   devices=/dev/hde2,/dev/hdg2
ARRAY /dev/md0 level=raid0 num-devices=2 UUID=ce6fce20:6f8c9f5f:e9c31e89:cb0ae703
   devices=/dev/hde1,/dev/hdg1

```

Now i've checked the initrd to make sure it has the mdadm, raid0 and raid1 modules.

On reboot my raid 1 partitions are detected and enabled, but none of the raid 0 partitions are enabled. I have to enabled them manually with 

```
mdadm -A -s
```

Now is it that the partitions on the extra IDE controller haven't been probed yet?

Steve

---

### Post by RIOT on 2005-06-16
After reading the linked thread, I tried a few more things:

I modified the mdadm.conf file to list all partitions.

```

DEVICE /dev/sd[a-c]1

```

I modified fstab to point to /dev/enms/md1 instead of /dev/md1.  I also changed this in mdadm.conf.

Neither of these worked.  This evening I'll check my initrd to make sure I have adadm and raid5 modules.  If that doesn't work, I'm planning on trying dmraid to set this up.

---

### Post by alastair on 2005-06-16
It might be a udev issue.

You could get udev to automatically assume/create the device /dev/md0 by editing the file :

/etc/udev/links.conf

and add someting like :

M md0           b 9 0

Then reboot and check. Might be the issue ....

---

### Post by RIOT on 2005-06-16
[QUOTE=alastair]It might be a udev issue.

You could get udev to automatically assume/create the device /dev/md0 by editing the file :

/etc/udev/links.conf

and add someting like :

M md0           b 9 0

Then reboot and check. Might be the issue ....[/QUOTE]

Alright...  Before trying your suggestion, I changed the /etc/fstab and /etc/mdadm/mdadm.conf files to have /dev/md0 instead of /dev/evms/md0.  After modifying the /etc/udev/links.conf file like you suggested, I received the following error message at boot after the usual fsck.ext3 error (hit CTRL-D to continue boot).  

```

*Mounting local filesystems...
EXT-fs:  unable to read superblock
mount:  wrong fs type, bad option, bad superblock on /dev/md0
	missing codepage or other error
	(could this be the IDE device where you in 
	fact use ide-scsi so the sr0 or sda or so is needed?)
	In some cases useful info is found in syslog - 
	try dmesg | tail or so

```

/dev/md0 did not mount at all.  After getting into Gnome, I started a terminal and did the following commands:

```

$ sudo mdadm -A -s
Password:
mdadm: /dev/md0 has been started with 3 drives.

$ sudo mount /dev/md0

$ mount
/dev/hda1 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw)
sysfs on /sys type sysfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
tmpfs on /dev/shm type tmpfs (rw)
/dev on /.dev type unknown (rw,bind)
none on /dev type tmpfs (rw,size=5M,mode=0755)
usbfs on /proc/bus/usb type usbfs (rw)
/dev/md0 on /share type ext3 (rw)

$ df -T -h
Filesystem    Type    Size  Used Avail Use% Mounted on
/dev/hda1     ext3     18G  7.3G  9.5G  44% /
tmpfs        tmpfs    126M     0  126M   0% /dev/shm
/dev       unknown     18G  7.3G  9.5G  44% /.dev
none         tmpfs    5.0M  2.8M  2.3M  56% /dev
/dev/md0      ext3     16G   33M   15G   1% /share

```

So now I have everything mounted and running correctly...  as long as I don't reboot the computer...  LOL [-X

:edit:
I noticed in the /share directory there is now a lost+found directory.  Should I do anything with this or just leave it alone?

---

### Post by steven_ellis on 2005-06-16
Ok here is my /etc/mdadm/mdadm.conf and all of my raid sets now appear

```
DEVICE /dev/hd[abeg]*
ARRAY /dev/md4 level=raid1 num-devices=2 UUID=63b054c9:d6b959a4:7273d641:a28743ea
   devices=/dev/hdb6,/dev/hda6 auto=yes
ARRAY /dev/md3 level=raid1 num-devices=2 UUID=689f7488:a6bc5e47:42924063:c829c439
   devices=/dev/hdb5,/dev/hda5
ARRAY /dev/md2 level=raid1 num-devices=2 UUID=033ffaf5:fd7f595b:6996dd14:74c90456
   devices=/dev/hdb2,/dev/hda3 auto=yes
ARRAY /dev/md1 level=raid0 num-devices=2 UUID=fc4f146f:d72a5f00:4333e628:9247f19e
   devices=/dev/hde2,/dev/hdg2 auto=yes
ARRAY /dev/md0 level=raid0 num-devices=2 UUID=ce6fce20:6f8c9f5f:e9c31e89:cb0ae703
   devices=/dev/hde1,/dev/hdg1 auto=yes
``` 

Don't know if it was the DEVICE line or auto=yes that fixed it.

FYI  /dev/md3 is my root partition which always worked anyway.

Steve

---

### Post by RIOT on 2005-06-17
Glad yours is working now.  I tried adding auto=yes to the mdadm.conf file like you did, but it still didn't mount on boot.  

Is there a way to insert the command "mdadm -A -s"  before the computer tries to mount /dev/md0?  When I rebooted, I tried running "mount /dev/md0" and it gave the error:

```

*Mounting local filesystems...
EXT-fs:  unable to read superblock
mount:  wrong fs type, bad option, bad superblock on /dev/md0
	missing codepage or other error
	(could this be the IDE device where you in 
	fact use ide-scsi so the sr0 or sda or so is needed?)
	In some cases useful info is found in syslog - 
	try dmesg | tail or so

```

This is the same as when booting, so I'm thinking that the raid array is not being started before it is trying to boot.

---

