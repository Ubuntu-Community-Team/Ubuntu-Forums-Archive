---
title: "usbmount: mount USB disk always to the same mount point."
date: 2016-09-15
forum: Hardware
---

### Post by adriaan4 on 2016-09-15
Hello all,

I use usbmount to my great satisfaction, but I would like usbmount to mount a certain USB disk always to the same mountpoint. Reason: I want Kodi to find it's library after each restart. Can't find how. Any idea?

I know how to find UUID's etc, that is not the issue. On the web, a lo of solutions are served, but they use home-made scripts.

I just want to configure usbmount in the way that when I mount drive with UUID 1234, it will always mount it to /media/music

Thanks

Adriaan

---

### Post by reese1379 on 2016-09-16
Use [Gparted]("http://gparted.org/") to label the USB device 'music' and it'll be mounted in /media/username/music

a. Insert the USB device
b. Fire up Gparted
c. unmount the USB device
d. relabel the USB device
e. unplug and reinsert the USB device

---

### Post by adriaan4 on 2016-09-18
Hi Reese!

Thanks. That works. Although I needed to format the disk from Apple hfs+ to ext4. Then, I encountered a lot of permission problems. Therefore I also needed to adapt usbmount.conf somewhat, in order to adapt the default mount points. 

[FONT=courier new]MOUNTPOINTS="/media/music /media/usb0 /media/usb1 /media/usb2 /media/usb3
             /media/usb4 /media/usb5 /media/usb6 /media/usb7"[/FONT]

I know this only works with this particular USB disk mounted first to the computer, but that is no problem. [FONT=courier new][/FONT]

Maybe it would be nice we could config usbmount in such a way that we can *specify specific rules for known-UUID's* (permissions, mount points), and *general rules* for ad-hoc mounted devices.


Earlier, I used this in fstab:
[FONT=courier new]#UUID="ff36e37w-2222-5555-333-cccc" /media/music ext4 defaults 0 2 [/FONT]

Thanks again!

A

---

