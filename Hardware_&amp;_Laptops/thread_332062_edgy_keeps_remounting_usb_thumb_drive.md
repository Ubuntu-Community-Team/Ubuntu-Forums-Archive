---
title: "edgy keeps remounting usb thumb drive"
date: 2007-01-05
forum: Hardware &amp; Laptops
---

### Post by bottlekeynut on 2007-01-05
hey,

after i put my usb drive in, every time i click on 'eject' or 'unmount volume', the drive always remounts itself. if i try unplugging the drive in the brief period when it seems to be unmounted, i still get a warning message saying i shouldnt unplug a mounted volume. am i doing something wrong here?

thanks in advance

---

### Post by balak on 2007-01-05
Please make sure you are not accessing the files in the mounted volume when you are trying to unmount.

Even if you are in a terminal and are in that directory, it considers as accessing the volume.

If this happens again, can you post the output of dmesg to see whats the reason

COMMAND:
abracadaba@ubuntu$dmesg | tail -20

---

### Post by bottlekeynut on 2007-01-05
i dont appear to be accessing the drive in any way when i'm trying to unmount. when i right click on the usbdisk icon on the desktop and click 'eject', the icon briefly disappears, then reappears.

mesg gave me:

[18434609.628000] SCSI device sda: 127998 512-byte hdwr sectors (66 MB)
[18434609.636000] sda: Write Protect is off
[18434609.636000] sda: Mode Sense: 03 00 00 00
[18434609.636000] sda: assuming drive cache: write through
[18434609.668000] SCSI device sda: 127998 512-byte hdwr sectors (66 MB)
[18434609.676000] sda: Write Protect is off
[18434609.676000] sda: Mode Sense: 03 00 00 00
[18434609.676000] sda: assuming drive cache: write through
[18434609.676000]  sda: sda1
[18434610.128000] FAT: utf8 is not a recommended IO charset for FAT filesystems, filesystem will be case sensitive!
[18434633.768000] SCSI device sda: 127998 512-byte hdwr sectors (66 MB)
[18434633.776000] sda: Write Protect is off
[18434633.776000] sda: Mode Sense: 03 00 00 00
[18434633.776000] sda: assuming drive cache: write through
[18434633.820000] SCSI device sda: 127998 512-byte hdwr sectors (66 MB)
[18434633.824000] sda: Write Protect is off
[18434633.824000] sda: Mode Sense: 03 00 00 00
[18434633.824000] sda: assuming drive cache: write through
[18434633.828000]  sda: sda1
[18434634.180000] FAT: utf8 is not a recommended IO charset for FAT filesystems, filesystem will be case sensitive!

---

