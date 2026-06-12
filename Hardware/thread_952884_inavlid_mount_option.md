---
title: "inavlid mount option"
date: 2008-10-19
forum: Hardware
---

### Post by fierydwarf on 2008-10-19
hi guys im totally new to this linux thing lol, when i plug in my external usb hdd i get the following error - "invalid mount option when ttempting to mount the volume iomega-HDD"

fstab says
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda5
UUID=ff620afd-7b5a-4e5f-b51d-cf9e99ac65c9 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda6
UUID=aeb9895e-93c9-4660-9b33-c416095c0bd5 none            swap    sw              0       0
/dev/sdb1       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/scd0       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0

sudo fdisk -l says

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda5
UUID=ff620afd-7b5a-4e5f-b51d-cf9e99ac65c9 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda6
UUID=aeb9895e-93c9-4660-9b33-c416095c0bd5 none            swap    sw              0       0
/dev/sdb1       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/scd0       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0



another error that shows up is

DBus error org.freedesktop.DBus.Error.NoReply: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken

---

### Post by anystupidname on 2008-10-19
Can we see the REAL fdisk -l output? Looks like you copied the fstab contents twice twice instead.

Unplug drive
```
tail -f /var/log/messages
```
plug in drive
show us what it says

My guess is that "/dev/sdb1" is what the external drive is being seen as and "/media/cdrom0 udf,iso9660 user,noauto,exec,utf8 0 0" is definitely not valid for that drive... Either comment it out and let automounting occur, or modify that line to be correct. What fs is the partition?

---

### Post by fierydwarf on 2008-10-19
sorry, didnt notice that,

second attempt

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x032b5bd3

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        6438    51713203+   7  HPFS/NTFS
/dev/sda2            6439       14593    65505037+   5  Extended
/dev/sda5            6439       14255    62790021   83  Linux
/dev/sda6           14256       14593     2714953+  82  Linux swap / Solaris

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xaebe0312

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       60802   488385024    7  HPFS/NTFS


here u go

---

### Post by anystupidname on 2008-10-19
Looks like my guess was correct although you still seem to be skimming a bit too much. What happened to the tail -f /var/log/messages?

Suggest replace:
```
/dev/sdb1 /media/cdrom0 udf,iso9660 user,noauto,exec,utf8 0 0
```
with:```

UUID=<blah> /home/doofus ntfs-3g defaults 0 1
```

get uuid with:
```
vol_id /dev/sdb1
```

pre-create mountpoint folder if necessary:
```
mkdir /home/doofus
```

Cheers

---

### Post by fierydwarf on 2008-10-19
my apologies, im half asleep and i totally missed that part

Oct 19 22:19:11 phil-laptop kernel: [ 4665.568052] usb 5-5: new high speed USB device using ehci_hcd and address 12
Oct 19 22:19:11 phil-laptop kernel: [ 4665.783622] usb 5-5: configuration #1 chosen from 1 choice
Oct 19 22:19:12 phil-laptop kernel: [ 4665.801781] scsi12 : SCSI emulation for USB Mass Storage devices
Oct 19 22:19:17 phil-laptop kernel: [ 4670.848785] scsi 12:0:0:0: Direct-Access     ST350083 0A               3.AA PQ: 0 ANSI: 0
Oct 19 22:19:17 phil-laptop kernel: [ 4670.873294] sd 12:0:0:0: [sdb] 976773168 512-byte hardware sectors (500108 MB)
Oct 19 22:19:17 phil-laptop kernel: [ 4670.879654] sd 12:0:0:0: [sdb] Write Protect is off
Oct 19 22:19:17 phil-laptop kernel: [ 4670.899048] sd 12:0:0:0: [sdb] 976773168 512-byte hardware sectors (500108 MB)
Oct 19 22:19:17 phil-laptop kernel: [ 4670.900902] sd 12:0:0:0: [sdb] Write Protect is off
Oct 19 22:19:25 phil-laptop kernel: [ 4670.900920]  sdb: sdb1
Oct 19 22:19:25 phil-laptop kernel: [ 4679.005351] sd 12:0:0:0: [sdb] Attached SCSI disk
Oct 19 22:19:25 phil-laptop kernel: [ 4679.007964] sd 12:0:0:0: Attached scsi generic sg2 type 0
Oct 19 22:19:27 phil-laptop kernel: [ 4681.187798] UDF-fs: No partition found (1)
Oct 19 22:19:27 phil-laptop kernel: [ 4681.228142] ISOFS: Unable to identify CD-ROM format.

thats what come up when i plug in the drive, i havent tried your suggestion yet, thought i'd post this first.

cheers

---

### Post by anystupidname on 2008-10-19
See these 2 lines?
Oct 19 22:19:27 phil-laptop kernel: [ 4681.187798] UDF-fs: No partition found (1)
Oct 19 22:19:27 phil-laptop kernel: [ 4681.228142] ISOFS: Unable to identify CD-ROM format.

Everything I've suggested still applies. It is trying to mount NTFS as ISOFS which of course fails.

---

### Post by fierydwarf on 2008-10-19
ive followed your instructions  the fstab now says

# /etc/fstab: static file system information.
#
# <file system> <mount point> <type> <options> <dump> <pass>
proc /proc proc defaults 0 0
# /dev/sda5
UUID=ff620afd-7b5a-4e5f-b51d-cf9e99ac65c9 / ext3 relatime,errors=remount-ro 0 1
# /dev/sda6
UUID=aeb9895e-93c9-4660-9b33-c416095c0bd5 none swap sw 0 0
UUID=CCD002A9D0029A3A /home/doofus ntfs-3g defaults 0 1
/dev/scd0 /media/cdrom1 udf,iso9660 user,noauto,exec,utf8 0 0

tail -f /var/log/messages says

Oct 19 23:02:53 phil-laptop kernel: [  148.341606] type=1503 audit(1224453773.160:11): operation="socket_create" family="appletalk" sock_type="dgram" protocol=0 pid=6157 profile="/usr/sbin/cupsd"
Oct 19 23:02:53 phil-laptop kernel: [  148.341617] type=1503 audit(1224453773.160:12): operation="socket_create" family="econet" sock_type="dgram" protocol=0 pid=6157 profile="/usr/sbin/cupsd"
Oct 19 23:02:53 phil-laptop kernel: [  148.341633] type=1503 audit(1224453773.160:13): operation="socket_create" family="ash" sock_type="dgram" protocol=0 pid=6157 profile="/usr/sbin/cupsd"
Oct 19 23:03:03 phil-laptop kernel: [  158.536176] usb 5-5: new high speed USB device using ehci_hcd and address 3
Oct 19 23:03:03 phil-laptop kernel: [  158.753213] usb 5-5: configuration #1 chosen from 1 choice
Oct 19 23:03:03 phil-laptop kernel: [  158.754787] scsi3 : SCSI emulation for USB Mass Storage devices
Oct 19 23:03:08 phil-laptop kernel: [  163.791760] scsi 3:0:0:0: Direct-Access     ST350083 0A               3.AA PQ: 0 ANSI: 0
Oct 19 23:03:08 phil-laptop kernel: [  163.795110] sd 3:0:0:0: [sdb] 976773168 512-byte hardware sectors (500108 MB)
Oct 19 23:03:08 phil-laptop kernel: [  163.796435] sd 3:0:0:0: [sdb] Write Protect is off
Oct 19 23:03:08 phil-laptop kernel: [  163.802091] sd 3:0:0:0: [sdb] 976773168 512-byte hardware sectors (500108 MB)
Oct 19 23:03:08 phil-laptop kernel: [  163.803876] sd 3:0:0:0: [sdb] Write Protect is off
Oct 19 23:03:16 phil-laptop kernel: [  163.804810]  sdb: sdb1
Oct 19 23:03:16 phil-laptop kernel: [  171.453370] sd 3:0:0:0: [sdb] Attached SCSI disk
Oct 19 23:03:16 phil-laptop kernel: [  171.454848] sd 3:0:0:0: Attached scsi generic sg2 type 0


im no longer getting the error but the drive still is not mounting.i hope im not annoying you with all this but i reli have no clue as to what im doing.

---

### Post by anystupidname on 2008-10-19
Um, so the contents of /home/doofus is not accessible or is something else going wrong? What is the output of just plain mount?

```
mount
```

Just in case the UUID is wrong for some reason, try temporarily replacing "UUID=CCD002A9D0029A3A" with "LABEL=/dev/sdb1"

No problem, happy to help. I was once in your shoes.

---

### Post by fierydwarf on 2008-10-20
changing the line to "LABEL=/dev/sdb1" seems to have fixed the problem,the drive mounted as soon as i changed that line. thanks very much!!!

---

### Post by anystupidname on 2008-10-20
OK, sounds good. I'd still encourage you to get the UUID= working as the label can change and then it won't mount again and it won't be obvious why so you'll spend another hour tshooting that.
:lolflag:

---

