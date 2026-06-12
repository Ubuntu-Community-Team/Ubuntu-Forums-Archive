---
title: "Strange built-in webcam errors (HP Pavillion DV6000)"
date: 2007-09-07
forum: Hardware &amp; Laptops
---

### Post by whenelvisdied on 2007-09-07
Hi all,

I have been trying to get the built-in webcam on HP pavillion dv6000 laptop to work.  I have tried multiple drivers, and I keep bumping up against the same error.  The output of my lsusb is as follows:


Bus 002 Device 002: ID 03f0:171d Hewlett-Packard
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 003: ID 0c45:62c0 Microdia
Bus 001 Device 001: ID 0000:0000


I assume the Microdia is the webcam, though I can't be sure.  In that case, i have heard some people say that the spca5xx (or gspca) driver will work, others say that the UVC-video driver will work, and still others say that the R5u870 driver is the best.  

I have tried them all, and have found that they give me some version of the same error.  I can compile them all fine, they create the module, and then when I type 

*sudo modprobe DRIVERNAME*

I get a message that looks like this:  

*Unknown symbol in module, or unknown parameter (see dmesg)*

Upon looking in dmesg, I see something that looks like this:

DRIVERNAME:  Unknown symbol .....
DRIVERNAME:  disagrees about ....

and so on.  I feel like this must be some kind of unmet dependency, or something that I haven't installed, since it's happened on three different drivers.  

I run ubuntu feisty, with the generic kernel.  

Any help would be appreciated....

---

### Post by deaf_girl on 2007-09-07
I found this. Hope it can help

[https://wiki.ubuntu.com/hp_dv6000_series_(dv6116eu)#head-1c7180cbcc04dae94420ec64f775311b0fe93bf2]("https://wiki.ubuntu.com/hp_dv6000_series_(dv6116eu)#head-1c7180cbcc04dae94420ec64f775311b0fe93bf2")

---

### Post by whenelvisdied on 2007-09-07
> **deaf_girl said:**
> I found this. Hope it can help

[https://wiki.ubuntu.com/hp_dv6000_series_(dv6116eu)#head-1c7180cbcc04dae94420ec64f775311b0fe93bf2]("https://wiki.ubuntu.com/hp_dv6000_series_(dv6116eu)#head-1c7180cbcc04dae94420ec64f775311b0fe93bf2")

This is actually the most recent thing I've tried. I was able to load two of the packages, but the third had a requirement of libc6 > 2.6, and the most recent feisty version is 2.5.  I would just upgrade anyway, but am worried about crashing.  Any advice on this?

---

### Post by whenelvisdied on 2007-09-10
Okay...so I did try the above webpage, and after installing the various packages, it still gave me the same error (symbol, etc..)

Here's dmesg after trying to load the UVC drivers:

[ 3425.947416] uvcvideo: disagrees about version of symbol v4l_compat_translate_ioctl
[ 3425.947423] uvcvideo: Unknown symbol v4l_compat_translate_ioctl
[ 3425.947540] uvcvideo: disagrees about version of symbol video_devdata
[ 3425.947542] uvcvideo: Unknown symbol video_devdata
[ 3425.947770] uvcvideo: disagrees about version of symbol video_unregister_device
[ 3425.947772] uvcvideo: Unknown symbol video_unregister_device
[ 3425.947845] uvcvideo: disagrees about version of symbol video_device_alloc
[ 3425.947847] uvcvideo: Unknown symbol video_device_alloc
[ 3425.947907] uvcvideo: disagrees about version of symbol video_register_device
[ 3425.947909] uvcvideo: Unknown symbol video_register_device
[ 3425.948024] uvcvideo: disagrees about version of symbol video_usercopy
[ 3425.948026] uvcvideo: Unknown symbol video_usercopy
[ 3425.948053] uvcvideo: disagrees about version of symbol video_device_release
[ 3425.948055] uvcvideo: Unknown symbol video_device_release

Any    help would be appreciated....

---

