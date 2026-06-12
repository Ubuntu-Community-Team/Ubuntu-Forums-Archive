---
title: "SonyEricsson Xperia Arc USB problem"
date: 2011-04-13
forum: Hardware
---

### Post by Snorkr on 2011-04-13
Hi.

I just got a brand new Xperia Arc running Android 2.3 (Gingerbread). I also run 10.10 on an iMac. Usually I don't have any problems connecting usb devices to the iMac. My old Nokia N86 connected without problems (as a USB disk). Now, when I connect the Arc to the iMac I get:

```
[535484.028139] usb 1-1: usbfs: USBDEVFS_CONTROL failed cmd gvfs-gphoto2-vo rqt 192 rq 8 len 1000 ret -110
[535484.033234] scsi 12:0:0:0: CD-ROM            SEMC     CD-ROM           0100 PQ: 0 ANSI: 2
[535484.037506] sr1: scsi3-mmc drive: 0x/0x caddy
[535484.039550] sr 12:0:0:0: Attached scsi CD-ROM sr1
[535484.042325] sr 12:0:0:0: Attached scsi generic sg2 type 5
[535485.031623] usb 1-1: usbfs: USBDEVFS_CONTROL failed cmd gvfs-gphoto2-vo rqt 192 rq 8 len 1000 ret -110
[535495.469054] usb 1-1: reset high speed USB device using ehci_hcd and address 17
[535519.861051] usb 1-1: reset high speed USB device using ehci_hcd and address 17
[535544.024045] usb 1-1: reset high speed USB device using ehci_hcd and address 17

```

Then after a while I get a popup "Media player device error Unable to open the (null)(null) device"

I tried to connect the Arc to a Win 7 machine and it popped up as an USB drive without problems.

Any thoughts?

Thanks in advance, 
-S

---

### Post by kntyskw on 2011-05-01
I just got the same problem and found your post here :)

I noticed my Xperia arc was configured to use MTP mode when connected to a usb host. I changed it to MSC and the problem was solved. If you are ok with MSC mode, you could do the same.

1. Go to Settings-> Sony Ericsson -> Connection
2. Tap USB connection mode and choose MSC

Note: The above menu item names could be different on yours since I'm using it in Japanese language.

---

### Post by Luggy on 2011-05-03
> **kntyskw said:**
> I just got the same problem and found your post here :)

I noticed my Xperia arc was configured to use MTP mode when connected to a usb host. I changed it to MSC and the problem was solved. If you are ok with MSC mode, you could do the same.

1. Go to Settings-> Sony Ericsson -> Connection
2. Tap USB connection mode and choose MSC

Note: The above menu item names could be different on yours since I'm using it in Japanese language.

I tried that solution with my Xperia Arc but I am still not having any luck. I have it in MSC mode but it doesn't pop-up as a flash drive or anything. The disk utility can see a SEMC Mass Storage device but it cannot see the media.

Any thoughts?

---

### Post by pandamancer on 2011-06-26
Here's what you need to do:

(Before you do this, take note that apps that were moved to SD will disappear as the SD card needs to be unmounted!!!)

To mount:

 1. Connect the device via usb
 2. Go to notification, Set the USB connection mode to MSC (SEMC should pop up)
 3. Again in notification > connect phone memory card (this step will unmount your SD card). 
 4. Wait until the notification in the device tells you that the phone memory card is connected. After that, the SEMC storage can now be accessed.

To unmount:

 1. Go to notification > phone memory card connected > disconnect
 2. Wait till a notification is received, your apps should return as usual

This works with ubuntu lucid version

Hope this helps!

---

### Post by northwolf on 2012-11-10
> **kntyskw said:**
> I just got the same problem and found your post here :)

I noticed my Xperia arc was configured to use MTP mode when connected to a usb host. I changed it to MSC and the problem was solved. If you are ok with MSC mode, you could do the same.

1. Go to Settings-> Sony Ericsson -> Connection
2. Tap USB connection mode and choose MSC

Note: The above menu item names could be different on yours since I'm using it in Japanese language.

SAME Menu and THANK YOU... it worked for me!!!
While still plugged in, I changed to MSC and right away the connect message came up in UBUNTU.
Thanks Again!

---

### Post by Makibronze on 2012-11-30
Changing MTP to MSC will do nothing unless you haven't installed Wine. Use Ubuntu Software Center to install it. Then you change USB connection mode to MSC in your phone settings and check PC companion. Ubuntu recognized my Sony Ericsson Experia Arc S after I did that.

---

### Post by howefield on 2012-11-30
Old thread back to sleep.

---

