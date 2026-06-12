---
title: "HP CD4E usb cd-writer not working"
date: 2005-05-09
forum: Hardware &amp; Laptops
---

### Post by macaetano on 2005-05-09
Hi! 

Since I booted Ubuntu for the first time that I'm having problems with my HP USB CD-writer, a CD4E unit. The drive is recognized by the system but it gives me the same permanent error:

May  9 21:22:20 localhost kernel: Additional sense: Invalid command operation code
May  9 21:22:20 localhost kernel: SCSI device sda: 4294967295 512-byte hdwr sectors (2199023 MB)
May  9 21:22:20 localhost kernel: sda: test WP failed, assume Write Enabled
May  9 21:22:20 localhost kernel:  /dev/scsi/host0/bus0/target0/lun0:<3>Buffer I/O error on device sda, logical block 0
May  9 21:22:20 localhost kernel:  unable to read partition table

And then it continues repeating this same message: 

Buffer I/O error on device sda, logical block 7
Buffer I/O error on device sda, logical block 0
Buffer I/O error on device sda, logical block 1
Buffer I/O error on device sda, logical block 2
Buffer I/O error on device sda, logical block 3
Buffer I/O error on device sda, logical block 4
Buffer I/O error on device sda, logical block 5
Buffer I/O error on device sda, logical block 6
Buffer I/O error on device sda, logical block 7
 unable to read partition table

I've been searching for a solution to this problem but until now I haven't found any. I wish someone could help me in a straight and direct way. Thanks in advance for the help.

---

