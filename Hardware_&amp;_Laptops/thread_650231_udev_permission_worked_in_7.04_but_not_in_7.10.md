---
title: "udev permission worked in 7.04 but not in 7.10"
date: 2007-12-26
forum: Hardware &amp; Laptops
---

### Post by ZDemon on 2007-12-26
Hi guys, I'm still quite new to using udev.

I'm using an Altera USB-Blaster for my work. Until recently, it worked fine in 7.04. However, it doesn't seem to work in 7.10. This is the permission i used in 7.04 :

```

# Altera USB-Blaster
BUS=="usb", SYSFS{idVendor}=="09fb", SYSFS{idProduct}=="6001", MODE="0666", SYMLINK+="usbblaster"

```

I put the above line at the end of the 40-permissions.rules file in the udev directory. Can anyone spot anything wrong or unusual? Or perhaps point out what is different in Ubuntu 7.10?

The program just doesn't seem to detect my USB-Blaster. Any help is appreciated.

Thanks in advance.

BTW : here is the link from the manufacturer on how to get it working in Red Hat (Ubuntu is not supported and they told me to buzz off)
[http://www.altera.com/support/software/drivers/dri-usb_b-lnx.html]("http://www.altera.com/support/software/drivers/dri-usb_b-lnx.html")

---

### Post by ZDemon on 2007-12-27
Bump. Anyone?

---

### Post by ZDemon on 2007-12-27
Hi guys, i got it fixed by mounting usbfs with permission 0666 in /etc/fstab

Is this dangerous? Please comment.

Thanks.

---

### Post by flybywire on 2008-02-06
ZDemon hi

I had the same problem. Also solved (partially) by editing fstab but the permissions do not work.

I put in the line:

/dev/bus/usb /proc/bus/usb usbfs defaults 0 0

What does your change to fstab look like. How do you set the permission there?

When I type jtagconfig I get:

1) USB_Blaster [USB 4-1.2]
  Unable to lock chain (Insufficient port permissions)

tx

---

