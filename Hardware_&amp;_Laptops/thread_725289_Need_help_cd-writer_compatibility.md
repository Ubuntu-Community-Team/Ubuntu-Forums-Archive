---
title: "Need help cd-writer compatibility"
date: 2008-03-15
forum: Hardware &amp; Laptops
---

### Post by kamacat7 on 2008-03-15
Hi! I have an internal cd-writer Waitec saurus, my ubuntu show the cd-writer in the file browser; but I can't read any cd's... while in the windows xp partition I can read and write cd's; I searched for in the official list of hardware but I can't find anything about Waitec.
 Help because Ubuntu is fantastic, and  I'll never leave it.

---

### Post by prshah on 2008-03-15
> **kamacat7 said:**
> Hi! I have an internal cd-writer Waitec saurus, my ubuntu show the cd-writer in the file browser; but I can't read any cd's... while in the windows xp partition I can read and write cd's; I searched for in the official list of hardware but I can't find anything about Waitec.
 Help because Ubuntu is fantastic, and  I'll never leave it.

Waitec is a supported model, but I don't know your model number. Why not try to burn a CD and then post the result of ```
dmesg | tail -15
```? That will give us a clue where things are going wrong. While you are at it, a brief configuration summary would also help.

---

### Post by kamacat7 on 2008-03-15
Thanks for answering; when you say model number do you refer to the serial number?

My hardware config (desktop pc) : cpu amd duron 1,2 ghz; ram 512 Mb hdd: 80 Gb; hdd on primary master, cd-rw (ata) on primary slave. About MBR: /dev/hda1 for ntfs, /dev/hda2 for ext3, /dev/hda3 for extended, /dev/hda5 for swap and 5Gb unallocated. Linux ubuntu gutsy gibbon 1.4 and the system is up to date

  In the file browsers when  I double click on cd-rw icon It send this message "cdda:///dev/hdb is not a valid location" . 

 I can not burn cd's not even explore them. Please comment  if I'm doing errors in configurating my pc or whatever...
 Thank you,thank you

---

### Post by SuprNoodles on 2008-03-15
Sounds somewhat similar to my problem. Works fine on Windows, though on Ubuntu, seems to be some input/output issues: [http://ubuntuforums.org/showthread.php?t=725226](http://ubuntuforums.org/showthread.php?t=725226)

---

### Post by kamacat7 on 2008-03-24
Actually I can not open cd's
 I logged as root and I tryed to mount the volume, with these results:

root@pc:~# mount -F iso9660 /dev/hdb
mount: special device iso9660 does not exist
root@pc:~# dmesg | tail -n 20
[ 3836.606791] ide: failed opcode was: unknown
[ 3836.608026] hdb: error code: 0x70  sense_key: 0x05  asc: 0x64  ascq: 0x00
[ 3836.608037] end_request: I/O error, dev hdb, sector 835264
[ 3836.938636] hdb: command error: status=0x51 { DriveReady SeekComplete Error }
[ 3836.938651] hdb: command error: error=0x50 { LastFailedSense=0x05 }
[ 3836.938656] ide: failed opcode was: unknown
[ 3836.939924] hdb: error code: 0x70  sense_key: 0x05  asc: 0x64  ascq: 0x00
[ 3836.939939] end_request: I/O error, dev hdb, sector 1248
[ 3836.944834] hdb: command error: status=0x51 { DriveReady SeekComplete Error }
[ 3836.944846] hdb: command error: error=0x50 { LastFailedSense=0x05 }
[ 3836.944850] ide: failed opcode was: unknown
[ 3836.946307] hdb: error code: 0x70  sense_key: 0x05  asc: 0x64  ascq: 0x00
[ 3836.946316] end_request: I/O error, dev hdb, sector 1024
[ 3836.946579] UDF-fs: No partition found (1)
[ 3836.965331] hdb: command error: status=0x51 { DriveReady SeekComplete Error }
[ 3836.965344] hdb: command error: error=0x50 { LastFailedSense=0x05 }
[ 3836.965350] ide: failed opcode was: unknown
[ 3836.966822] hdb: error code: 0x70  sense_key: 0x05  asc: 0x64  ascq: 0x00
[ 3836.966835] end_request: I/O error, dev hdb, sector 64
[ 3836.967099] isofs_fill_super: bread failed, dev=hdb, iso_blknum=16, block=16


About model number, do you refer to the serial number? Because the model is simply "Saurus" by Waitec.

Thank you all for answering..

---

### Post by kamacat7 on 2008-03-24
And this is my fstab:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda2
UUID=f3dae596-119f-4093-b816-31ce6c4077e4 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda5
UUID=d5d850d8-3c7e-4b83-8b55-b94d8c100cba none            swap    sw              0       0
/dev/hdb        /media/cdrom0    udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0

Hi to everyone

---

