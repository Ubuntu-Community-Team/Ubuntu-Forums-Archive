---
title: "&gt;2Tb HDD in 8.10 Server"
date: 2009-05-14
forum: Hardware
---

### Post by ccreese on 2009-05-14
Hello all.

I'm trying to install a LaCie 4big quadra 6TB, but my 8.10 server will not recognize it as anything but 2Tb. 

I used gparted to format what it sees as ext3, and 

sudo fdisk -l 

gives:

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       18657   149862321   83  Linux
/dev/sdb2           18658       19452     6385837+   5  Extended
/dev/sdb5           18658       19452     6385806   82  Linux swap / Solaris

Disk /dev/sdc: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000098ec

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1      121601   976760001   83  Linux

Disk /dev/sdh: 2199.0 GB, 2199023255552 bytes
255 heads, 63 sectors/track, 267349 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000d7db9

   Device Boot      Start         End      Blocks   Id  System
/dev/sdh1               1      267349  2147480811   83  Linux

If I run parted and 'print devices' I get:

/dev/sda (1000GB)
/dev/sdb (160GB)
/dev/sdc (1000GB)
/dev/sdh (2199GB)

I know that the file system size is limited to 2TB with blocks of size 1024 .. and presumably LBD support would allow me to have a larger file system. 

Running through the options of the kernel (2.6.27-11-server), however, I do not see an option for LBD under the Block Devices category. 

Any ideas?

Thanks,
Colin

---

### Post by Dark_Stang on 2009-05-14
Uhm...
[http://en.wikipedia.org/wiki/Ext3#Size_limits](http://en.wikipedia.org/wiki/Ext3#Size_limits)

Edit: I'd recommend just formatting it into something else. ext4 will support up to 1 exabyte.

---

### Post by ccreese on 2009-05-15
Yes, but parted lists the physical size of the volume, not the partition - sdh, not sdh1 - so this appears to be a kernel problem of drive support.

---

### Post by ccreese on 2009-05-18
bump. 

Seriously, nobody has succeeded in mounting a volume >2Tb? Hard to believe, considering data backup and storage is one of the primary functions of a server.

---

### Post by ccreese on 2009-05-20
Ok, so circumvent the kernel limitation, I simply installed a hardware raid controller: 

[http://www.lacie.com/us/products/product.htm?pid=11217](http://www.lacie.com/us/products/product.htm?pid=11217)

This worked, is plug and play, faster than the firewire I was using, and will allow extension using additional SATA drives, should I choose to.

---

