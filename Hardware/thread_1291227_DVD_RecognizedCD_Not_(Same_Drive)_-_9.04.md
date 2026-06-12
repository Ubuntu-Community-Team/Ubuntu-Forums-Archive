---
title: "DVD Recognized/CD Not (Same Drive) - 9.04"
date: 2009-10-14
forum: Hardware
---

### Post by poorbadger on 2009-10-14
**Edit 20091016: For the archives - this turned out to be a hardware versus software issue**.

I have a combo CD-RW/DVD-ROM on a Thinkpad T61p.  As of 8.10 I was able to insert audio & data CDs and DVDs and have them auto-mount and play.

Upgraded to 9.04 a while ago and the drive quit working.  I don't use it everyday so I didn't recognize it right away.  Wrote it off to probably bad hardware.

Yesterday I got tired of shuffling things around by USB to another machine to extract and burn and started digging around.

Turns out the DVD side of things works fine.  Put a DVD in - it shows up on the desktop and prompts me to play or not.

CDs - either data or audio just kind of click around (never actually spins up) and fails to mount either automatically or through GUI or CLI.  Multiple audio CDs tested - all purchased and official.

I've done all the requisite searches but nothing so far has seemed to work nor did I find anything specifically where one format works but another doesn't.

Any ideas?

fstab & udev - 70-persistent-cd.rules

```

user@machine:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=36630ab6-4dec-44a4-b681-5c215f93f307 /               ext3    defaults,errors=remount-ro,relatime 0       1
# /dev/sda2
UUID=1431da9b-270e-4bf9-96de-ac56dd017c96 /home           ext3    defaults,relatime        0       2
# /dev/sda3
UUID=9df50733-59d1-4dc2-af8b-70595f7e896b none            swap    sw              0       0
# CD-RW/DVD
/dev/scd0	/media/cdrom0	udf,iso9660	user,noauto,exec,utf8	0	0

user@machine:/etc/udev/rules.d$ cat 70-persistent-cd.rules 
# This file maintains persistent names for CD/DVD reader and writer devices.
# See udev(7) for syntax.
#
# Entries are automatically added by the 75-persistent-cd-generator.rules
# file; however you are also free to add your own entries provided you
# add the ENV{GENERATED}=1 flag to your own rules as well.
# RWDVD_GCC-4247N (pci-0000:00:1f.1-scsi-0:0:0:0)
ENV{ID_CDROM}=="?*", ENV{ID_PATH}=="pci-0000:00:1f.1-scsi-0:0:0:0", SYMLINK+="cdrom", ENV{GENERATED}="1"
ENV{ID_CDROM}=="?*", ENV{ID_PATH}=="pci-0000:00:1f.1-scsi-0:0:0:0", SYMLINK+="cdrw", ENV{GENERATED}="1"
ENV{ID_CDROM}=="?*", ENV{ID_PATH}=="pci-0000:00:1f.1-scsi-0:0:0:0", SYMLINK+="dvd", ENV{GENERATED}="1"

```

early dmesg output related to CD-ROM
```

[    2.481621] scsi 3:0:0:0: CD-ROM            HL-DT-ST RW/DVD GCC-4247N 1.02 PQ: 0 ANSI: 5
[    2.492716] sr0: scsi3-mmc drive: 24x/24x writer cd/rw xa/form2 cdda tray
[    2.492718] Uniform CD-ROM driver Revision: 3.20
[    2.492788] sr 3:0:0:0: Attached scsi CD-ROM sr0
[    2.492819] sr 3:0:0:0: Attached scsi generic sg1 type 5

```

dmesg & mtab after inserting DVD
```

user@machine:~$ dmesg | grep UDF
[  717.521162] UDF-fs: Partition marked readonly; forcing readonly mount
[  717.554610] UDF-fs INFO UDF: Mounting volume 'EMBRYONIC', timestamp 2009/08/31 16:54 (1000)

user@machine:~$ cat /etc/mtab 
/dev/sda1 / ext3 rw,relatime,errors=remount-ro 0 0
tmpfs /lib/init/rw tmpfs rw,nosuid,mode=0755 0 0
proc /proc proc rw,noexec,nosuid,nodev 0 0
sysfs /sys sysfs rw,noexec,nosuid,nodev 0 0
varrun /var/run tmpfs rw,nosuid,mode=0755 0 0
varlock /var/lock tmpfs rw,noexec,nosuid,nodev,mode=1777 0 0
udev /dev tmpfs rw,mode=0755 0 0
tmpfs /dev/shm tmpfs rw,nosuid,nodev 0 0
devpts /dev/pts devpts rw,noexec,nosuid,gid=5,mode=620 0 0
fusectl /sys/fs/fuse/connections fusectl rw 0 0
lrm /lib/modules/2.6.28-15-generic/volatile tmpfs rw,mode=755 0 0
/dev/sda2 /home ext3 rw,relatime 0 0
securityfs /sys/kernel/security securityfs rw 0 0
nfsd /proc/fs/nfsd nfsd rw 0 0
binfmt_misc /proc/sys/fs/binfmt_misc binfmt_misc rw,noexec,nosuid,nodev 0 0
gvfs-fuse-daemon /home/user/.gvfs fuse.gvfs-fuse-daemon rw,nosuid,nodev,user=user 0 0
/dev/sr0 /media/cdrom0 udf ro,nosuid,nodev,utf8,user=user 0 0

```

lshw - without CD inserted and then with.
Note status does change.
```

user@machine:/etc/udev/rules.d$ sudo lshw -c disk
  *-cdrom                 
       description: DVD reader
       product: RW/DVD GCC-4247N
       vendor: HL-DT-ST
       physical id: 0.0.0
       bus info: scsi@3:0.0.0
       logical name: /dev/cdrom
       logical name: /dev/cdrw
       logical name: /dev/dvd
       logical name: /dev/scd0
       logical name: /dev/sr0
       version: 1.02
       capabilities: removable audio cd-r cd-rw dvd
       configuration: ansiversion=5 status=nodisc

user@machine:/etc/udev/rules.d$ sudo lshw -c disk
  *-cdrom                 
       description: DVD reader
       product: RW/DVD GCC-4247N
       vendor: HL-DT-ST
       physical id: 0.0.0
       bus info: scsi@3:0.0.0
       logical name: /dev/cdrom
       logical name: /dev/cdrw
       logical name: /dev/dvd
       logical name: /dev/scd0
       logical name: /dev/sr0
       version: 1.02
       capabilities: removable audio cd-r cd-rw dvd
       configuration: ansiversion=5 status=ready
     *-medium
          physical id: 0
          logical name: /dev/cdrom

```

dmesg - after inserting CD
```

user@machine:/$ dmesg | tail
[ 2097.989972] Buffer I/O error on device sr0, logical block 0
[ 2097.989979] Buffer I/O error on device sr0, logical block 1
[ 2097.989982] Buffer I/O error on device sr0, logical block 2
[ 2097.989986] Buffer I/O error on device sr0, logical block 3
[ 2097.989997] Buffer I/O error on device sr0, logical block 0
[ 2097.990010] Buffer I/O error on device sr0, logical block 0
[ 2097.990025] Buffer I/O error on device sr0, logical block 0
[ 2097.990036] Buffer I/O error on device sr0, logical block 0
[ 2097.990046] Buffer I/O error on device sr0, logical block 0
[ 2097.990064] Buffer I/O error on device sr0, logical block 0

```

Misc
```

user@machine:/$ sudo mount /media/cdrom/
mount: no medium found on /dev/sr0

user@machine:/dev$ ls -al sr0
brw-rw----+ 1 root cdrom 11, 0 2009-10-14 10:10 sr0

user@machine:~$ uname -a
Linux machine 2.6.28-15-generic #52-Ubuntu SMP Wed Sep 9 10:49:34 UTC 2009 i686 GNU/Linux

```

---

### Post by Giblet5 on 2009-10-14
It sounds like a major coincidence, but maybe the drive died around the time you upgraded.

Put a Live CD in there (Intrepid, Jaunty, whatever) and see if you can boot from it. That's about as good a test as you'll get.

---

### Post by prshah on 2009-10-14
> **poorbadger said:**
> 
fstab & udev - 70-persistent-cd.rules

From Hardy onwards, fstab should no longer have entries for dynamic devices such as optical and removable drives.

I don't know if this is the problem, but it might be worth commenting out the line related to the CD/DVD drive in /etc/fstab, rebooting and then checking the drive.

Buffer I/O errors are generally indicative of bad media, but as you say that you have tried various CDs, I guess this is unlikely; maybe a bad laser? (But one that works with DVDs?)

---

### Post by Giblet5 on 2009-10-14
> **prshah said:**
> From Hardy onwards, fstab should no longer have entries for dynamic devices such as optical and removable drives.

I don't know if this is the problem, but it might be worth commenting out the line related to the CD/DVD drive in /etc/fstab, rebooting and then checking the drive.

Buffer I/O errors are generally indicative of bad media, but as you say that you have tried various CDs, I guess this is unlikely; maybe a bad laser? (But one that works with DVDs?)

+1 on all of that

Most DVD drives use the same laser for DVD or CD media, but alter the focus for one or the other. Sometimes the focus mechanism gets stuck due to dirt and one media type or the other will stop working.

An air can and a gentle whack or three might shake it loose if that's the problem.

---

### Post by poorbadger on 2009-10-14
Thanks for the suggestions everyone.

[LIST]
[*]Removed /dev/scd0 from fstab & rebooted.  Auto-recognized DVD. CD still not working.
[*]Blasted some canned air around.  Same CD problem persists.
[*]Rebooted w/ a 9.04 Live CD because I had one around.  Lots of CD chatter but the machine gave up and booted to Hard Drive.
[*]In process of downloading 8.04 to burn on another machine and attempt booting from that.  I'll let you know how that turns out.
[/LIST]

Looked the machine up on Lenovo's site and it's still under warranty so I'll likely be giving them a call after the 8.04 boot test to hear what they have to say.

Thanks again!

---

### Post by poorbadger on 2009-10-14
8.04 wouldn't boot from CD either so it looks like it's a hardware issue in this case.

Lenovo is sending out a replacement unit tomorrow (Yea Lenovo).

Thanks again for the help Giblet5 & prshah.

---

### Post by dandnsmith on 2009-10-15
> **Giblet5 said:**
> Most DVD drives use the same laser for DVD or CD media, but alter the focus for one or the other. Sometimes the focus mechanism gets stuck due to dirt and one media type or the other will stop working.

Are you sure about that? I'd appreciate a tech reference.
I understood that CD and DVD used different frequency lasers, and one of these can go defective. I do realise that a lot of common optical path is used, so you only see one end path.

---

### Post by poorbadger on 2009-10-16
New Hardware arrived this morning.  CD Read/Write & DVD Read verified.  So this one was a hardware issue.

Thanks.

> **poorbadger said:**
> 8.04 wouldn't boot from CD either so it looks like it's a hardware issue in this case.

Lenovo is sending out a replacement unit tomorrow (Yea Lenovo).

Thanks again for the help Giblet5 & prshah.

---

