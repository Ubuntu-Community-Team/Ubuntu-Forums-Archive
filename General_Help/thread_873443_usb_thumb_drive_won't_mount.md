---
title: "usb thumb drive won't mount"
date: 2008-07-29
forum: General Help
---

### Post by mattduckman on 2008-07-29
hello,

i just bought a Transcend JF V30 USB thumb drive, and ubuntu is having problems accessing it. here's the output from dmesg when i plug it in:

```

[ 3573.782753] usb 5-5: new high speed USB device using ehci_hcd and address 4
[ 3573.917308] usb 5-5: configuration #1 chosen from 1 choice
[ 3573.918631] scsi3 : SCSI emulation for USB Mass Storage devices
[ 3573.918631] usb-storage: device found at 4
[ 3573.918631] usb-storage: waiting for device to settle before scanning
[ 3578.938175] usb-storage: device scan complete
[ 3578.939087] scsi scan: INQUIRY result too short (5), using 36
[ 3578.939087] scsi 3:0:0:0: Direct-Access                                    PQ: 0 ANSI: 0
[ 3578.957483] sd 3:0:0:0: [sdb] Sector size 0 reported, assuming 512.
[ 3578.957483] sd 3:0:0:0: [sdb] 1 512-byte hardware sectors (0 MB)
[ 3578.957862] sd 3:0:0:0: [sdb] Write Protect is off
[ 3578.957862] sd 3:0:0:0: [sdb] Mode Sense: 03 00 00 00
[ 3578.957862] sd 3:0:0:0: [sdb] Assuming drive cache: write through
[ 3578.958522] sd 3:0:0:0: [sdb] Sector size 0 reported, assuming 512.
[ 3578.958522] sd 3:0:0:0: [sdb] 1 512-byte hardware sectors (0 MB)
[ 3578.958985] sd 3:0:0:0: [sdb] Write Protect is off
[ 3578.958991] sd 3:0:0:0: [sdb] Mode Sense: 03 00 00 00
[ 3578.958996] sd 3:0:0:0: [sdb] Assuming drive cache: write through
[ 3578.959004]  sdb: sdb1
[ 3579.059879]  sdb: p1 exceeds device capacity
[ 3579.059879] sd 3:0:0:0: [sdb] Attached SCSI disk
[ 3579.059879] sd 3:0:0:0: Attached scsi generic sg2 type 0
[ 3579.102431] attempt to access beyond end of device
[ 3579.102431] sdb: rw=0, want=8200, limit=1
[ 3579.102431] Buffer I/O error on device sdb1, logical block 0
[ 3579.102431] attempt to access beyond end of device
[ 3579.102431] sdb: rw=0, want=8208, limit=1
[ 3579.102431] Buffer I/O error on device sdb1, logical block 1
[ 3579.102431] attempt to access beyond end of device
[ 3579.102431] sdb: rw=0, want=8216, limit=1
[ 3579.102431] Buffer I/O error on device sdb1, logical block 2
[ 3579.102431] attempt to access beyond end of device
[ 3579.102431] sdb: rw=0, want=8224, limit=1
[ 3579.102431] Buffer I/O error on device sdb1, logical block 3
[ 3579.102431] attempt to access beyond end of device
[ 3579.102431] sdb: rw=0, want=8200, limit=1
[ 3579.102431] Buffer I/O error on device sdb1, logical block 0
[ 3579.113500] attempt to access beyond end of device
[ 3579.113500] sdb: rw=0, want=8200, limit=1
[ 3579.113500] Buffer I/O error on device sdb1, logical block 0
[ 3579.113500] attempt to access beyond end of device
[ 3579.113500] sdb: rw=0, want=8208, limit=1
[ 3579.113500] Buffer I/O error on device sdb1, logical block 1
[ 3579.113500] attempt to access beyond end of device
[ 3579.113500] sdb: rw=0, want=8216, limit=1
[ 3579.113500] Buffer I/O error on device sdb1, logical block 2
[ 3579.113500] attempt to access beyond end of device
[ 3579.113500] sdb: rw=0, want=8224, limit=1
[ 3579.113500] Buffer I/O error on device sdb1, logical block 3
[ 3579.113500] attempt to access beyond end of device
[ 3579.113500] sdb: rw=0, want=8200, limit=1
[ 3579.113500] Buffer I/O error on device sdb1, logical block 0
[ 3663.255372] usb 5-5: USB disconnect, address 4
[ 3665.803849] usb 5-7: new high speed USB device using ehci_hcd and address 5
[ 3665.936593] usb 5-7: configuration #1 chosen from 1 choice
[ 3666.022160] scsi4 : SCSI emulation for USB Mass Storage devices
[ 3666.039219] usb-storage: device found at 5
[ 3666.039219] usb-storage: waiting for device to settle before scanning
[ 3671.054202] usb-storage: device scan complete
[ 3671.054446] scsi scan: INQUIRY result too short (5), using 36
[ 3671.054446] scsi 4:0:0:0: Direct-Access                                    PQ: 0 ANSI: 0
[ 3671.077284] sd 4:0:0:0: [sdb] Sector size 0 reported, assuming 512.
[ 3671.077284] sd 4:0:0:0: [sdb] 1 512-byte hardware sectors (0 MB)
[ 3671.077763] sd 4:0:0:0: [sdb] Write Protect is off
[ 3671.077775] sd 4:0:0:0: [sdb] Mode Sense: 03 00 00 00
[ 3671.077781] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[ 3671.081282] sd 4:0:0:0: [sdb] Sector size 0 reported, assuming 512.
[ 3671.081282] sd 4:0:0:0: [sdb] 1 512-byte hardware sectors (0 MB)
[ 3671.081282] sd 4:0:0:0: [sdb] Write Protect is off
[ 3671.081282] sd 4:0:0:0: [sdb] Mode Sense: 03 00 00 00
[ 3671.081282] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[ 3671.081282]  sdb: sdb1
[ 3671.183776]  sdb: p1 exceeds device capacity
[ 3671.183776] sd 4:0:0:0: [sdb] Attached SCSI disk
[ 3671.183776] sd 4:0:0:0: Attached scsi generic sg2 type 0
[ 3671.225166] attempt to access beyond end of device
[ 3671.225179] sdb: rw=0, want=8200, limit=1
[ 3671.225183] Buffer I/O error on device sdb1, logical block 0
[ 3671.225553] attempt to access beyond end of device
[ 3671.225553] sdb: rw=0, want=8208, limit=1
[ 3671.225553] Buffer I/O error on device sdb1, logical block 1
[ 3671.225553] attempt to access beyond end of device
[ 3671.225553] sdb: rw=0, want=8216, limit=1
[ 3671.225553] Buffer I/O error on device sdb1, logical block 2
[ 3671.228031] attempt to access beyond end of device
[ 3671.228037] sdb: rw=0, want=8224, limit=1
[ 3671.228040] Buffer I/O error on device sdb1, logical block 3
[ 3671.228500] attempt to access beyond end of device
[ 3671.228506] sdb: rw=0, want=8200, limit=1
[ 3671.228509] Buffer I/O error on device sdb1, logical block 0
[ 3671.240919] attempt to access beyond end of device
[ 3671.240919] sdb: rw=0, want=8200, limit=1
[ 3671.240919] Buffer I/O error on device sdb1, logical block 0
[ 3671.240919] attempt to access beyond end of device
[ 3671.240919] sdb: rw=0, want=8208, limit=1
[ 3671.240919] Buffer I/O error on device sdb1, logical block 1
[ 3671.241317] attempt to access beyond end of device
[ 3671.241323] sdb: rw=0, want=8216, limit=1
[ 3671.241326] Buffer I/O error on device sdb1, logical block 2
[ 3671.241766] attempt to access beyond end of device
[ 3671.241771] sdb: rw=0, want=8224, limit=1
[ 3671.241774] Buffer I/O error on device sdb1, logical block 3
[ 3671.242209] attempt to access beyond end of device
[ 3671.242215] sdb: rw=0, want=8200, limit=1
[ 3671.242218] Buffer I/O error on device sdb1, logical block 0

```

mount, fsck, mkfs, and fdisk all fail. windows xp, however, has no problem with it. can anybody help me out with this?

thanks,
matt

---

### Post by PmDematagoda on 2008-07-29
Does:-
```
fdisk -l
```
show the proper statistics of the drive?

---

### Post by mattduckman on 2008-07-29
nope, it says "Unable to read /dev/sdb"

---

### Post by 3vi1 on 2008-08-26
I have the exact same problem with a Transcend JetFlash V10 (16GB) USB thumbdrive that I bought yesterday:  It will mount fine in Windows and Kubuntu 8.04, but refuses to mount under 8.10-alpha4 (but the same Intrepid installation can access other USB devices - including a 4GB thumbdrive - fine).

It seems to be a bug in the 2.6.26 kernel?  :(

I haven't found anything that can be done about it so far.  8.10 won't even let you get into fdisk with it, and trying to dd over the partition table fails.  I deleted/recreated the partition table and formatted it as Ext2 using my 8.04 machine (2.6.24-16 kernel), which has no complaints about it.  It continues to work fine on 8.04, yet refuses to be accessible (fdisk -l = 'unable to read /dev/sdc') on the 8.10 machine.  :(

I'm searching around to see if this is already a known bug on launchpad.  I have yet to find an exact match, but some of the things seen in the description of [https://bugs.launchpad.net/ubuntu/+source/hal/+bug/251781](https://bugs.launchpad.net/ubuntu/+source/hal/+bug/251781) make me believe it's possibly the same problem.  If I don't find a better match, I'm going to add info there.

lsusb reports the drive as:  Bus 002 Device 006: ID 058f:6387 Alcor Micro Corp. Transcend JetFlash Flash Drive

---

### Post by deletarus on 2008-10-15
I'm still getting this issue in 8.10 beta. I get "invalid mount option..." when I insert the drive. I am using an 8GB PNY. my sudo fdisk -l reports that it is indeed 8GB.

I have tried updating several time, I have re-installed hal and gnome-volume-manager and nothing has worked. Has anyone else found a solution?

---

