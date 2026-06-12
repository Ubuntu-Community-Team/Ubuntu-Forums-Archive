---
title: "Unable to mount SATA drive"
date: 2007-05-21
forum: Hardware &amp; Laptops
---

### Post by Clontarf[X] on 2007-05-21
Hi Guys,

Been playing about with Kubunutu (Dapper) and after a few hiccups finally got my nForce based motherboard, with SATA, humming along swimmingly.

However, I am encountering an issue mounting a drive that I have never come across, nor have I found anything that helps.

Information:

nForce 430 based motherboard (ASUS M2N-MX)
SATA2 - 250GB WD

I am unable to mount this drive, and as far as I know the fstab and everything else are fine

Here is my obligatory configuration information;

> [COLOR="Red"]shane@klonnyserver:~$ sudo mount /dev/sda1
mount: /dev/sda1 already mounted or /media/sda1 busy[/COLOR]

> shane@klonnyserver:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc /proc proc defaults 0 0
/dev/hda1 /media/hda1 auto users,atime,auto,rw,dev,exec,suid,umask=000 0 0
/dev/hdb1 / ext3 nouser,defaults,errors=remount-ro,atime,auto,rw,dev,exec,suid 0 1
/dev/sda1 /media/sda1 auto users,atime,auto,rw,dev,exec,suid,umask=000 0 0
/dev/scd0 /media/cdrom0 udf,iso9660 users,atime,noauto,rw,dev,exec,suid 0 0
> shane@klonnyserver:~$ cat /etc/mtab
/dev/hdb1 / ext3 rw,errors=remount-ro 0 0
proc /proc proc rw 0 0
/sys /sys sysfs rw 0 0
varrun /var/run tmpfs rw 0 0
varlock /var/lock tmpfs rw 0 0
udev /dev tmpfs rw 0 0
devpts /dev/pts devpts rw,gid=5,mode=620 0 0
devshm /dev/shm tmpfs rw 0 0
/dev/hda1 /media/hda1 ntfs rw,umask=000 0 0
shane@klonnyserver:~$


As you can see, /dev/sda1 is definately not mounted. The only thing that has changed is I recently did a kernel recompile. Is there anything that I might of broken to cause this? Maybe the SATA is no longer /dev/sd? What's the easiest way of finding out where my drive is hiding?

Thanks!

 - Shane

---

### Post by kaptainlange on 2007-05-21
Hrm.  You could check /var/log/udev to see what devices were created.

Look for blocks that have:
DEVNAME=/dev/sd*

In those same sections, there should be:
ID_MODEL=Your_Hard_drive_model

That will confirm whether or not the sata drives are at /dev/sd* .

---

### Post by Clontarf[X] on 2007-05-21
Found the entry in uev, but it says /dev/sda1 ... so at least I know I have that bit right :)

Any other ideas?

> UDEV  [1179710520.471020] add@/block/sda/sda1
UDEV_LOG=3
ACTION=add
DEVPATH=/block/sda/sda1
SUBSYSTEM=block
SEQNUM=3017
MINOR=1
MAJOR=8
PHYSDEVPATH=/devices/pci0000:00/0000:00:08.0/host0/target0:0:0/0:0:0:0
PHYSDEVBUS=scsi
PHYSDEVDRIVER=sd
UDEVD_EVENT=1
ID_VENDOR=ATA
ID_MODEL=WDC_WD2500JS-60M
ID_REVISION=10.0
ID_SERIAL=1ATA_WDC_WD2500JS-60MHB1_WD-WCANK51
ID_TYPE=disk
ID_BUS=scsi
ID_PATH=pci-0000:00:08.0-scsi-0:0:0:0
ID_FS_USAGE=filesystem
ID_FS_TYPE=ntfs
ID_FS_VERSION=3.1
ID_FS_UUID=C89CF5309CF51A20
ID_FS_LABEL=Setup
ID_FS_LABEL_SAFE=Setup_Files
DEVNAME=/dev/sda1
DEVLINKS=/dev/disk/by-id/scsi-1ATA_WDC_WD2500JS-60MHB1_WD-WCANK51-part1 /dev/disk/by-path/pci-0000:00:08.0-scsi-0:0:0:0-part1 /dev/disk/by-uuid/C89CF5309CF51A20 /dev/disk/by-label/Setup_Files

Additionally, I receive the following from the Disk & Filesystems Configuration panel in "System Settings"

> Return code from mount was 32.
"mount failure"

---

### Post by kaptainlange on 2007-05-21
```
# /etc/fstab: static file system information.
#
# <file system> <mount point> <type> <options> <dump> <pass>
proc /proc proc defaults 0 0
/dev/hda1 /media/hda1 auto users,atime,auto,rw,dev,exec,suid,umask=000 0 0
/dev/hdb1 / ext3 nouser,defaults,errors=remount-ro,atime,auto,rw,dev,exec,suid 0 1
#Comment out the original line and add the new line below
#/dev/sda1 /media/sda1 auto users,atime,auto,rw,dev,exec,suid,umask=000 0 0
/dev/sda1 /media/sda1 ntfs defaults,nls=utf-8,umask=007,gid=46 0 1
#End changes
/dev/scd0 /media/cdrom0 udf,iso9660 users,atime,noauto,rw,dev,exec,suid 0 0
```

Try making those changes to your /etc/fstab .  You've got writing as well as updating access times on an NTFS drive.  We're gonna try mounting it read only for the time being, last I checked writing on NTFS was flakey under linux.

Unmount the /dev/sda1 point, and then remount it.  See if that works.

---

### Post by Clontarf[X] on 2007-05-21
I attempted the change above, and still no luck. I did however reboot the PC, and moved the SATA connector to SATA3 (/dev/sdc1, if it followed the naming convention).

However I noticed that no device exists in /dev with that name, and /dev/sda and sda1 were still there... and they still give the same errors...

Any other ideas?

---

### Post by Clontarf[X] on 2007-05-21
Additionally, I have tested a /home mount point (i.e ~/test), which still fails, with obviously the path changing. This leads me to believe there is something not right about the SATA implementation, or that I need to figure out why it thinks /dev/sda1 is mounted...

I still welcome any ideas!

---

### Post by kaptainlange on 2007-05-21
> **'Clontarf[X] said:**
> Additionally, I have tested a /home mount point (i.e ~/test), which still fails, with obviously the path changing. This leads me to believe there is something not right about the SATA implementation, or that I need to figure out why it thinks /dev/sda1 is mounted...

I still welcome any ideas!

This is about the time I would turn to the Ubuntu Forums for some help, heh.  I'd also start doing some search for the motherboard + linux to see if anyone else is having similar issues with your mobo.

Also, just thought, maybe the filesystem is corrupt on that partition?  Though I imagine since it's ntfs that you're using it under windows as well with no issue?

---

### Post by Clontarf[X] on 2007-05-21
> **kaptainlange said:**
> Also, just thought, maybe the filesystem is corrupt on that partition?  Though I imagine since it's ntfs that you're using it under windows as well with no issue?

Yep, as I type this post I am currently in Vista and its accessing the drive without issue, and a chkdsk finds no problems... I just dont understand why it stopped working! Is there any lock files I should be looking for, or that the kernel looks for to see if a volume is mounted?

(edit) after doing some reading, I ensured I only had one SATA module enabled (nv_sata). I also tried removing all sata modules and let libsata do it's thing. Nothing is making any difference...

I need my music! Help!

---

### Post by Clontarf[X] on 2007-05-21
FIXED!!!!!!!!!!!!!!

After some more extensive searching *hugs google.com/linux* I found the culprit!

[COLOR="Red"]md-mapper, md-mod and dm[/COLOR]

If you have a drive that WILL NOT MOUNT regardless of what you try to do, and it errors with;
[COLOR="Red"]
shane@klonnyserver:~$ sudo mount /dev/sda1
mount: /dev/sda1 already mounted or /media/sda1 busy[/COLOR]

REMOVE THESE MODULES FROM YOUR KERNEL!

I did this, recompiled, rebooted, and all my drives are now automounted and KDE is happily accessing them.

God I love the Linux community :)

Thanks Kaptain!

---

