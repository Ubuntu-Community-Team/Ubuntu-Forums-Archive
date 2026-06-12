---
title: "[SOLVED] Help with &amp;quot;webcam&amp;quot; (and the webcam itself)"
date: 2008-05-28
forum: Hardware
---

### Post by LinuX-M@n1@k on 2008-05-28
Here's the error I get:
```
$ webcam /etc/webcam.conf
reading config file: /etc/webcam.conf
invalid norm: pal
$
$ sudo su
# webcam /etc/webcam.conf
reading config file: /etc/webcam.conf
invalid norm: pal
#
```

/etc/webcam.conf:
> 
[www]
dir = /var/www/htdocs
file = webcamoutput.jpg
local = 1

[grab]
device = /dev/video1
width = 352
height = 288
delay = 1
norm = pal
quality = 100

**The webcam I'm using: "Trust 120 SpaceCam"**

Last night it worked fine, but for some reason it's not working any more. I'm sure it has to do something with the modules "sn9c102" and/or "gspca"

lsmod:
```
$ lsmod | grep sn9c102
sn9c102               127236  0 
videodev               29440  5 gspca,sn9c102,cx8800,cx88xx
compat_ioctl32          2304  2 sn9c102,cx8800
v4l2_common            18304  5 sn9c102,tuner,cx8800,cx88xx,videodev
usbcore               146028  5 gspca,sn9c102,ehci_hcd,uhci_hcd
$
$ lsmod | grep gspca
gspca                 643920  1 
videodev               29440  5 gspca,sn9c102,cx8800,cx88xx
usbcore               146028  5 gspca,sn9c102,ehci_hcd,uhci_hcd
$
```

I also tried to reload these modules, but nothing happens:
```
# rmmod gspca
# rmmod sn9c102
# modprobe gspca
# modprobe sn9c102
```

Any help will be appreciated! Thanks.

**EDIT:** New error!
```
$ webcam /etc/webcam.conf
reading config file: /etc/webcam.conf
v4l2: open /dev/video1: No space left on device
v4l2: open /dev/video1: No space left on device
v4l: open /dev/video1: No space left on device
no grabber device available
$
```
I have no idea what happened!

**System Specs:**
Ubuntu 8.04 "Hardy Heron"
Kernel - 2.6.24-16-generic

---

### Post by LinuX-M@n1@k on 2008-05-28
.

---

### Post by ppihus on 2011-11-29
[SOLVED]?

WHERE is the solution then?

---

