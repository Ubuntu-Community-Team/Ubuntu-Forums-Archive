---
title: "USB device insertion hangs the system"
date: 2006-10-24
forum: Hardware &amp; Laptops
---

### Post by saisho on 2006-10-24
Hi,

I'm having a problem with USB detection on Ubuntu 6.06. Whenever I plug in a USB device the system freezes / hangs and I need to do a power switch reset. I've tried to tail /var/log/messages or dmesg but nothing is logged. My USB ports are detected ok (according to dmesg. The USB ports are on a PCI card). If I boot up with a USB device inserted (USB stick or camera), then the device is detected ok and I can access it. It only freezes when I'm inserting it while the system is already up and running. I suspect it might be IRQ conflict of some sort but have no idea what to do next.

Any idea? 

Thanks,

---

### Post by xyz on 2006-10-24
Hi saisho,
What does it read when in a termainal as root you run:
```
mount

or
df
```

Here is mine (3 partitions on external HD)
> /dev/sda1 on /media/usbdisk type vfat (rw,nosuid,nodev,quiet,shortname=mixed,uid=1000,gid=1000,umask=007,iocharset=utf8)
/dev/sda2 on /media/usbdisk-1 type vfat (rw,nosuid,nodev,quiet,shortname=mixed,uid=1000,gid=1000,umask=007,iocharset=utf8)
/dev/sda3 on /media/LOCAL DISK type vfat (rw,nosuid,nodev,quiet,shortname=mixed,uid=1000,gid=1000,umask=007,iocharset=utf8)


It mounts anywhere, anytime.

---

### Post by saisho on 2006-10-24
Mine says:

/dev/sda1 on /media/usbdisk type vfat (rw,nosuid,nodev,quiet,shortname=mixed,uid=1000,gid=1000,umask=077,iocharset=utf8)

This is when the USB stick is inserted before booting up Ubuntu as if I insert it when the system is already up, the system freezes.

Cheers,

---

### Post by burgermann on 2006-10-25
My computer does exactly the same. I've tried booton with acpi=off and noapci but none of these options seems to work. I'm running PCLinuxOS .93 which uses the 2.6.16-23 version, since Ubuntu doesn't work. Here everything (except WEP wlan) works perfectly, so I really wonder what the Ubuntu folks did that screws my laptop up.

The problem also occurs in Edgy, so it seems I'm stuck with PCLinuxOS for a quite a while.

---

### Post by saisho on 2007-04-29
[RESOLVED]
Upgraded to 7.04, run dmseg and noticed that ACPI says ACPI (1999) before cut off (2000) use acpi=force. 
Added acpi=force to menu.lst and voila - USB stick is now recognized without a problem.

---

