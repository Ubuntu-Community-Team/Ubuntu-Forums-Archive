---
title: "ipod mounting problem"
date: 2008-06-27
forum: Hardware
---

### Post by keirlawson on 2008-06-27
Hello,

I have an od problem with my Ipod,

When I insert the ipod, an error message is displayed in a window: "Invalid mount option when attempting to mount the volume 'IPOD'.". However, if i manually mound the device as root, it mounts fine, however the permissions as such that a normal user cannot write to it.  Here is dmesg | tail -n 10: 

> keir@cid:~$ dmesg | tail -n 30
[   97.215273] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[   99.359624] NET: Registered protocol family 17
[  107.564068] eth0: no IPv6 routers present
[  123.841675] eth0: no IPv6 routers present
[  285.215165] tun0: Disabled Privacy Extensions
[  881.745953] usb 7-1: new high speed USB device using ehci_hcd and address 3
[  881.879382] usb 7-1: configuration #1 chosen from 2 choices
[  882.006949] usbcore: registered new interface driver libusual
[  882.030335] Initializing USB Mass Storage driver...
[  882.030465] scsi5 : SCSI emulation for USB Mass Storage devices
[  882.030580] usbcore: registered new interface driver usb-storage
[  882.030582] USB Mass Storage support registered.
[  882.030763] usb-storage: device found at 3
[  882.030764] usb-storage: waiting for device to settle before scanning
[  882.496311] usb-storage: device scan complete
[  882.502397] scsi 5:0:0:0: Direct-Access     Apple    iPod             1.62 PQ: 0 ANSI: 0
[  882.512303] sd 5:0:0:0: [sdb] 19488471 4096-byte hardware sectors (79825 MB)
[  882.513054] sd 5:0:0:0: [sdb] Write Protect is off
[  882.513061] sd 5:0:0:0: [sdb] Mode Sense: 68 00 00 08
[  882.513066] sd 5:0:0:0: [sdb] Assuming drive cache: write through
[  882.515918] sd 5:0:0:0: [sdb] 19488471 4096-byte hardware sectors (79825 MB)
[  882.516915] sd 5:0:0:0: [sdb] Write Protect is off
[  882.516922] sd 5:0:0:0: [sdb] Mode Sense: 68 00 00 08
[  882.516926] sd 5:0:0:0: [sdb] Assuming drive cache: write through
[  882.517703]  sdb: sdb1
[  882.533571] sd 5:0:0:0: [sdb] Attached SCSI removable disk
[  882.533973] sd 5:0:0:0: Attached scsi generic sg2 type 0
[  883.029168] UDF-fs: No VRS found
[  883.068089] grow_buffers: requested out-of-range block 18446744071562067968 for device sdb1
[  883.068093] isofs_fill_super: bread failed, dev=sdb1, iso_blknum=17, block=-2147483648
keir@cid:~$ 


I dont know if any of that there is relevant.

---

### Post by phidia on 2008-06-27
To get your iPod working in linux-check [this howto]("http://ubuntuforums.org/showthread.php?t=103071&highlight=hfsplus+write") and hope that's helpful.

---

### Post by keirlawson on 2008-06-27
Nothing in that link was really much help...

---

### Post by phidia on 2008-06-27
Which version of ubuntu are you using, and can you mount any usb devices?
There is a bug report on gutsy about that but it's from last year.
A more recent bug report & fix is [here]("https://bugs.launchpad.net/ubuntu/+source/gnome-mount/+bug/151025").
The one for gutsy is [here]("https://bugs.launchpad.net/ubuntu/+source/gnome-mount/+bug/130490").
I don't if any of that is helpful but it's what comes up from searching the error output you posted.

---

