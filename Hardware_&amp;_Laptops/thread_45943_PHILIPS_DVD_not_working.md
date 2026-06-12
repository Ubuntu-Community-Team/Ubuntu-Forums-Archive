---
title: "PHILIPS DVD not working"
date: 2005-07-02
forum: Hardware &amp; Laptops
---

### Post by arangel on 2005-07-02
I bought a brand new PHILIPS DVD/RW  and installed it in my tower. Restarted and the result is: It only mounts full DVD's, I can watch DVD movies, and read content of of them. What I can't do is mount empty DVD-R's and I cannot burn any DVD-R's. In "Computer" I can see only "CD-ROM" and that get's mounted when I insert a full DVD. First I couldn't mount even DVD's with content but then I changed the entry in fstab from my older (now removed) CD-ROM which was /dev/hdc to /devhdd and that works now. I get this in syslog when trying to mount a blank DVD-R:

 kernel: attempt to access beyond end of device
 kernel: hdd: rw=0, want=68, limit=4
 kernel: attempt to access beyond end of device
 kernel: hdd: rw=0, want=1252, limit=4
 kernel: attempt to access beyond end of device
 kernel: hdd: rw=0, want=1028, limit=4
 kernel: UDF-fs: No partition found (1)
 kernel: attempt to access beyond end of device
 kernel: hdd: rw=0, want=68, limit=4
 kernel: isofs_fill_super: bread failed, dev=hdd, iso_blknum=16, block=16

This is the output of  dmesg | grep DVD:

hdd: PHILIPS PBDV1640P, ATAPI CD/DVD-ROM drive
hdd: ATAPI 63X DVD-ROM DVD-R CD-R/RW drive, 2048kB Cache

Also, K3b and GnomeToaster can see the DVD drive but when I try to burn smth I get a bunch of errors and that's it.

Using latest hoary kernel.

HELP! :0

---

### Post by arangel on 2005-07-04
This is the error from GnomeToaster:

:-[ PERFORM OPC failed with SK=4h/ASC=09h/ACQ=00h]: Input/output error
mkisofs: Broken pipe. cannot fwrite 6144*1

I'm going crazy here, I'm going out to buy a baseball bat and deal with the DVD/RW that way.  :mad:

---

