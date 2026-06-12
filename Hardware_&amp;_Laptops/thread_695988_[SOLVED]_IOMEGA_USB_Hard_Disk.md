---
title: "[SOLVED] IOMEGA USB Hard Disk"
date: 2008-02-13
forum: Hardware &amp; Laptops
---

### Post by opossumjack on 2008-02-13
Hi...
I'm using Ubuntu gutsy..
I just made a fresh installation. My external hard disk drive does not appear in the hard disk list in gparted. It is turned on and is working correctly on other machines. It is NTFS formatted. 

I also checked in /etc/fstab. It does not appear there too. 

I had edgy installed on my computer previously and the Hd was working fine. 

Anyone got ideas on how to mount (automatically) this hd? and why it does not appear anywhere?

Thanks in advance for your help..

---

### Post by taurus on 2008-02-13
Open a terminal and post the outputs of these two commands from a terminal.

Applications -> Accessories -> Terminal
```
dmesg | tail 
sudo fdisk -l
```

p.s.  Make sure the drive is plugged in and on.

---

### Post by cjay on 2008-02-14
Hi :)
I also have the same problem but my drive is a 40Gb USB "Storex Club pocket disk".
**formatted ntfs**
I have performed the commands as directed and this is my output from the terminal;
:(
root@XXXXX:/home/XXXXX# dmesg | tail
[  239.141322] PPP BSD Compression module registered
[  239.180530] PPP Deflate Compression module registered
[  885.562694] usb 6-3: new high speed USB device using ehci_hcd and address 3
[  885.696897] usb 6-3: configuration #1 chosen from 1 choice
[  885.697229] scsi4 : SCSI emulation for USB Mass Storage devices
[  885.697374] usb-storage: device found at 3
[  885.697376] usb-storage: waiting for device to settle before scanning
[  890.689960] usb-storage: device scan complete
[  896.462068] usb 6-3: USB disconnect, address 3
[  896.462192] scsi 4:0:0:0: scsi: Device offlined - not ready after error recovery
root@XXXXX:/home/XXXXX# sudo fdisk -l

Disk /dev/hdc: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xf1295cce

   Device Boot      Start         End      Blocks   Id  System
/dev/hdc1   *           1       30024   241167748+  83  Linux
/dev/hdc2           30025       30401     3028252+   5  Extended
/dev/hdc5           30025       30401     3028221   82  Linux swap / Solaris
root@XXXXX:/home/XXXXX# 
:confused:

**The device is recognized by windows and is writable to in windows**

---

### Post by opossumjack on 2008-02-16
I'm sorry but the computer with the hd is at my work site.. in these days I'm in bed with flu... :(

I ask you a little bit of patience... 
thanks a lot in advance..

I post the terminal commands as soon as possible..

---

