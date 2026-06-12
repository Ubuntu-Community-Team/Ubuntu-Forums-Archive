---
title: "/dev/hdc mount error"
date: 2006-02-11
forum: Hardware &amp; Laptops
---

### Post by reckless2k2 on 2006-02-11
I know this is probably something simple. This is the error I receive trying to access mdeia on cdrom:

Unable to mount the selected volume. The volume is probably in a format that cannot be mounted.

mount: block device /dev/hdc is write-protected, mounting read-only
mount: wrong fs type, bad option, bad superblock on /dev/hdc,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

---

### Post by taurus on 2006-02-11
Try 

sudo mount -t iso9660 /dev/hdc /media/cdrom0

Otherwise, look at your dmesg as the error states.  Open a terminal and at the prompt, type

dmesg | tail

---

### Post by reckless2k2 on 2006-02-11
More details from dmesg | tail:

[4333913.763000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4333959.838000] hdc: command error: status=0x51 { DriveReady SeekComplete Error }
[4333959.838000] hdc: command error: error=0x54 { AbortedCommand LastFailedSense=0x05 }
[4333959.838000] ide: failed opcode was: unknown
[4333959.838000] end_request: I/O error, dev hdc, sector 64
[4333959.840000] isofs_fill_super: bread failed, dev=hdc, iso_blknum=16, block=16
[4334045.038000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4334045.038000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4334045.184000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4334045.184000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.

from /etc/fstab:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda3       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda1       /media/hda1     ntfs    nls=utf8,umask=0222        0       0
/dev/hda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

---

### Post by reckless2k2 on 2006-02-12
Thanks taurus but that did not help. In the previous post I noted the results of dmesg | tail. Hopefully someone can provide assistance.

---

### Post by taurus on 2006-02-12
What kind of CD are you trying to mount here?

---

