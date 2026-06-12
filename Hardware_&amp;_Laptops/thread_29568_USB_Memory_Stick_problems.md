---
title: "USB Memory Stick problems"
date: 2005-04-24
forum: Hardware &amp; Laptops
---

### Post by Ironfrost on 2005-04-24
Hi,

I'm having some problems with a USB pendrive - Ubuntu doesn't seem to be automatically mounting it the same as it should do. The disk itself seems to be fine, as it works on Windows (2k / XP) and MacOS X. And I don't think it's a general problem with reading USB devices, as the memorystick in my camera shows up on the desktop when I plug it into the same USB port.

The device is recognised in Device Manager, and shows up as:

 - Unknown (0x8006)
 - - USB Mass Storage Interface
 - - - SCSI Host Interface
 - - - - SCSI Device
 - - - - - USB Flash Drive

You can probably see this better in the screenshot I have attatched (also, you can probably see the information in there that I haven't realised is important to post).


I guess that what I might be asking could be something as simple as "how do I mount this USB disk?". But maybe it is something more complex. I'm really not sure.

Thanks in advance everyone!

---

### Post by Unhandled_Exception on 2005-04-24
Hi,

From that screenshot it looks like it hasn't seen a volume on the device.  Can you also provide the output of /var/log/messages as the device is plugged in.  The manufacturer of the device etc.  Can you also type in a terminal "killall -15 gnome-volume-manager" and then enter "gnome-volume-manager 2>&1" and then provide the output of that command as the device is plugged in.

The data given seems to imply that no node was created for a volume on that device.  E.g. /dev/sda but no partition number.  Check if that's the case.

Thanks.

---

### Post by Ironfrost on 2005-04-24
[QUOTE=Unhandled_Exception]Hi,

From that screenshot it looks like it hasn't seen a volume on the device.  Can you also provide the output of /var/log/messages as the device is plugged in.
[/quote]

Apr 25 03:29:00 localhost kernel: usb 1-1.1: new full speed USB device using uhci_hcd and address 6
Apr 25 03:29:00 localhost kernel: scsi2 : SCSI emulation for USB Mass Storage devices
Apr 25 03:29:00 localhost usb.agent[6765]:      usb-storage: already loaded
Apr 25 03:29:05 localhost kernel:   Vendor: Generic   Model: USB Flash Drive   Rev: 1.03
Apr 25 03:29:05 localhost kernel:   Type:   Direct-Access                      ANSI SCSI revision: 02
Apr 25 03:29:05 localhost kernel: Attached scsi removable disk sda at scsi2, channel 0, id 0, lun 0
Apr 25 03:29:05 localhost scsi.agent[6814]:      sd_mod: loaded sucessfully



> 
 The manufacturer of the device etc.


Not a brand I've heard of - I bought it for cheap last summer, and it has the URL [http://www.kpm.com.cn](http://www.kpm.com.cn) on it. Looking through their website I think it's [this model](http://www.kpm.com.cn/ArticleShow.asp?ArticleID=313), but I can't be sure.



> 
  Can you also type in a terminal "killall -15 gnome-volume-manager" and then enter "gnome-volume-manager 2>&1" and then provide the output of that command as the device is plugged in.


manager.c/925: New Device: /org/freedesktop/Hal/devices/usb_device_1043_8006_100_-1_noserial
manager.c/925: New Device: /org/freedesktop/Hal/devices/usb_usb_device_1043_8006_100_-1_noserial_0
manager.c/925: New Device: /org/freedesktop/Hal/devices/scsi_host_4
manager.c/925: New Device: /org/freedesktop/Hal/devices/scsi_4_0_0_0
manager.c/925: New Device: /org/freedesktop/Hal/devices/block_8_0



> 
The data given seems to imply that no node was created for a volume on that device.  E.g. /dev/sda but no partition number.  Check if that's the case.


I'm not sure how to check this (I'm still quite new to linux).

---

