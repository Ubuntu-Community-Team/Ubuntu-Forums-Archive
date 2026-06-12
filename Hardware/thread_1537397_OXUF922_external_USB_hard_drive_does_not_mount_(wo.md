---
title: "OXUF922 external USB hard drive does not mount (works with XP &amp; OS X)"
date: 2010-07-23
forum: Hardware
---

### Post by irrationalJohn on 2010-07-23
This is the first time I've used this forum and I'm not familiar with the categories. If there is better place to post this question, please point me towards it.

I recently purchased this [EzQuest Pro external drive enclosure]("http://www.ezq.com/product/offproductspec.php?id=18"). When I connect it via USB to my desktop when I've booted Windows XP, it works as expected. It also works fine when I attach it to a USB port on my MacBook running OS X 10.6.

However, when I try using it when the desktop is running either Windows 7 or Ubuntu 10.04, it does not work. I'm having absolutely no luck getting any information about how to solve this problem on the Windows side. Since the enclosure also does not work in Ubuntu I was hoping I might get some help in at least determining why the enclosure/drive does not mount in Ubuntu.

The enclosure does **not** require any special drivers. It is intended to function using the same "mass storage" USB drivers most external drives use. (That is certainly what it uses when it attaches to XP.)

My problem is that I don't know how to dig into the Linux/Ubuntu internals to drag out an understandable cause for the failure.  What can I do to dig deeper into why this is not working? 

An excerpt from kern.log of the log messages issued when I attempted to connect the enclosure follows below. All it tells me is that the enclosure/drive fails to mount because of "error -110" ... whatever the heck that might be. :rolleyes:

(FWIW, I have also posted this [question on superuser.com]("http://superuser.com/questions/164653/external-usb-attached-drive-works-in-windows-xp-but-not-in-windows-7-how-to-fix"). I mention this only because I may have mentioned something there that I forgot to include when I posted here.)

-irrational john

> [ 2684.240015] usb 1-2: new high speed USB device using ehci_hcd and address 22
[ 2684.393618] usb 1-2: configuration #1 chosen from 1 choice
[ 2684.395399] scsi17 : SCSI emulation for USB Mass Storage devices
[ 2684.395570] usb-storage: device found at 22
[ 2684.395572] usb-storage: waiting for device to settle before scanning
[ 2689.390412] usb-storage: device scan complete
[ 2689.390894] scsi 17:0:0:0: Direct-Access     Hitachi  HDT721010SLA360  ST6O PQ: 0 ANSI: 4
[ 2689.392237] sd 17:0:0:0: Attached scsi generic sg7 type 0
[ 2689.395269] sd 17:0:0:0: [sde] 1953525168 512-byte logical blocks: (1.00 TB/931 GiB)
[ 2689.395632] sd 17:0:0:0: [sde] Write Protect is off
[ 2689.395636] sd 17:0:0:0: [sde] Mode Sense: 11 00 00 00
[ 2689.395639] sd 17:0:0:0: [sde] Assuming drive cache: write through
[ 2689.412003] sd 17:0:0:0: [sde] Assuming drive cache: write through
[ 2689.412009]  sde: sde1 sde2
[ 2689.455759] sd 17:0:0:0: [sde] Assuming drive cache: write through
[ 2689.455765] sd 17:0:0:0: [sde] Attached SCSI disk
[ 2692.620017] usb 1-2: reset high speed USB device using ehci_hcd and address 22
[ 2707.740014] usb 1-2: device descriptor read/64, error -110
[ 2722.970103] usb 1-2: device descriptor read/64, error -110
[ 2723.200027] usb 1-2: reset high speed USB device using ehci_hcd and address 22
[ 2738.320019] usb 1-2: device descriptor read/64, error -110
[ 2753.550024] usb 1-2: device descriptor read/64, error -110
[ 2753.780020] usb 1-2: reset high speed USB device using ehci_hcd and address 22
[ 2758.810147] usb 1-2: device descriptor read/8, error -110
[ 2763.940142] usb 1-2: device descriptor read/8, error -110
[ 2764.170014] usb 1-2: reset high speed USB device using ehci_hcd and address 22
[ 2769.200141] usb 1-2: device descriptor read/8, error -110
[ 2774.330137] usb 1-2: device descriptor read/8, error -110
[ 2774.440069] usb 1-2: USB disconnect, address 22
[ 2774.440503] sd 17:0:0:0: Device offlined - not ready after error recovery

---

