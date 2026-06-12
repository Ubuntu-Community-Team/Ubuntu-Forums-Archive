---
title: "How to automount udf?"
date: 2015-08-20
forum: Hardware
---

### Post by Berwyn_Powell on 2015-08-20
Hello,

First of all, sorry if this question gets asked a lot, but I'm having some slight difficulties with udf dvds. When I insert the dvd the drive spins, but the disk isn&#8217;t mounted. When I try to mount the drive using Caja I get the error "Unable to mount location: Can't mount file".
I can manually mount the disk using ```
sudo mount -t udf /dev/sr0 /mnt
``` and can happily browse the contents. I would like to know if it is possible to get auto mounting working? I've got no entry for the DVD drive in my fstab file, but I've heard this is now redundant?

Thanks in advance, Bez

P.S. I'm running Ubuntu MATE 15.04 on a HTPC using Kodi so mounting through the terminal is difficult as I'm using a remote most of the time.

---

