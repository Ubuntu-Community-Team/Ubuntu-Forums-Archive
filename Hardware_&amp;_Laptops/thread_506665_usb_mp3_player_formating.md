---
title: "usb mp3 player formating"
date: 2007-07-22
forum: Hardware &amp; Laptops
---

### Post by DWE on 2007-07-22
Just bought a Samsung U3 MP3 Player.

Plugged it in, and Ubuntu 7.04 sees it in Hardware Information, but does not recognise it as a drive.

I am assuming that the Samsung needs formatting before Ubuntu will recognise it as a drive. I don't use Windows, only Ubuntu. So.... how do I format it? (if thats the problem?)

Thanx in advance

---

### Post by DWE on 2007-07-22
here's what /etc/fstab has to say:
/etc/fstab: static file system information. 
# 
# <file system> <mount point>   <type>  <options>       <dump>  <pass> 
proc            /proc           proc    defaults        0       0 
# /dev/hda1 
UUID=526e86bd-5ab9-4fee-a696-62241b75e308 /               ext3    defaults,errors=remount-ro 0       1 
# /dev/hda5 
UUID=7bd87eec-2b82-4fbc-8fe4-0b166536f46b none            swap    sw              0       0 
/dev/cdrom        /media/cdrom0   udf,iso9660 user,noauto     0       0 
/dev/           /media/floppy0  auto    rw,user,noauto  0       0 

and here's the relevant part of lshw 
*-usb UNCLAIMED 
                   description: Generic USB device 
                   product: Samsung YP-U3 
                   vendor: Samsung Electronics 
                   physical id: 1 
                   bus info: usb@1:1 
                   version: 2.20 
                   serial: CBBBF762AFF00000 
                   capabilities: usb-2.00 
                   configuration: maxpower=500mA speed=12.0MB

and lastly, here's tail -f /var/log/messages brfore and after removal
Jul 22 04:24:05 maggie-desktop kernel: [ 3460.590740] end_request: I/O error, dev hdd, sector 4 
Jul 22 04:24:05 maggie-desktop kernel: [ 3460.594274] hdd: tray open 
Jul 22 04:24:05 maggie-desktop kernel: [ 3460.596433] end_request: I/O error, dev hdd, sector 0 
Jul 22 04:24:05 maggie-desktop kernel: [ 3460.598669] hdd: tray open 
Jul 22 04:24:05 maggie-desktop kernel: [ 3460.600819] end_request: I/O error, dev hdd, sector 4 
Jul 22 04:24:05 maggie-desktop kernel: [ 3460.603362] hdd: tray open 
Jul 22 04:24:05 maggie-desktop kernel: [ 3460.605513] end_request: I/O error, dev hdd, sector 0 
Jul 22 04:24:05 maggie-desktop kernel: [ 3460.607754] hdd: tray open 
Jul 22 04:24:05 maggie-desktop kernel: [ 3460.609907] end_request: I/O error, dev hdd, sector 4 
Jul 22 04:33:26 maggie-desktop kernel: [ 4021.517992] usb 1-1: USB disconnect, address 2 
Jul 22 04:34:25 maggie-desktop kernel: [ 4079.713179] usb 2-1: new full speed USB device using ohci_hcd and address 2 
Jul 22 04:34:25 maggie-desktop kernel: [ 4079.929230] usb 2-1: configuration #1 chosen from 1 choice 

Please help!!!

---

