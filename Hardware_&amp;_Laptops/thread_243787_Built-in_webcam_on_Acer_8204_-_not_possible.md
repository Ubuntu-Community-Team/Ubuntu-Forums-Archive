---
title: "Built-in webcam on Acer 8204 - not possible?"
date: 2006-08-25
forum: Hardware &amp; Laptops
---

### Post by Belyel on 2006-08-25
Ok, prep yourselves for a long post.  I've been trying to get my built-in webcam to work for the last two days pretty much non-stop.  I am fairly certain that it's not possible to use in Linux yet, but maybe I missed something, so here goes:

I didn't know if linux even recognized that I had a webcam, so I was at a loss until I searched for webcam info here.  I checked *lsusb* which returned: ```
Bus 005 Device 002: ID 067b:3507 Prolific Technology, Inc. PL3507 ATAPI6 Bridge
Bus 005 Device 003: ID 046b:0892 Logitech, Inc.
.
.
.
``` and the rest of my USB ports are working but not occupied.  The first item is my external drive, which is working perfectly.

Knowing the bus and the device number might be helpful, but I haven't figured out how it is helpful yet (maybe a mount option??).  So I tried ```
lshw -businfo | grep usb
``` which showed me ```
.
.
.
usb@5:8            generic    USB2.0 Web Camera
``` not so helpful.  Again, based on what else I had found in the forums, I looked at the details of the "generic" device using *lshw -C generic*: ```
*-usb:1 UNCLAIMED
description: Generic USB device
product: USB2.0 Web Camera
vendor: Vimicro Corp.
physical id: 8
bus info: usb@5:8
version: 1.00
capabilities: usb-2.00
configuration: maxpower=200mA speed=480.0MB/s
```
which gave me the product and vendor for use with a modprobe.  I looked up the vendor/product code using google and it came up as a logitech quickcam (I knew that).  I tried the built-in quickcam module with and without the vendor and product tags to no avail, tried the usbvideo module and the vicam module, too.  After each modprobe, I used ```
sudo /etc/init.d/udev restart

lshw -businfo | grep usb
``` to see if the camera was recognized as a camera.  I also tried using ekiga, but it never detected the camera, either.

I moved on to using 3rd party modules, and built and installed the UVC module.  I got the same lack of results.  I read about the *spca5xx* module, and noticed that it was already installed on my system, so tried that, too.  No results.  I'm going to try to build a fresh spca5xx module as soon as I get internet on my laptop again so I can download the dependencies, but I have little hope because my camera is not listed on the supported hardware list on the *spca5xx* website.

I also checked my */dev* folder and there is no video* entry, so the camera hasn't successfully been found yet.

For reference, my system is an Acer Travelmate 8200 with a core duo T2500, ati x1600, 2gb, 120gb partitioned hdd (win/ubuntu).  Almost everything else is working in ubuntu.  This isn't a show-stopping device, but I would like to have it working if possible.  Please look at what I've tried and make some suggestions as to next steps.  Although I'm a n00b, i want to learn all this stuff.

---

### Post by Belyel on 2006-08-26
I always hate being the guy to bump his own posts, but i'm doing it anyway.  I tried installing the newest version of spca5xx using the tutorial [here]("http://www.ubuntuforums.org/showthread.php?t=239516&highlight=installing+spca5xx"), but had no love.  I'm wondering if using ndiswrapper with the windoze driver might work for this.  I previously used ndiswrapper for my wirelss in breezy, is it just a wireless driver utility or would it maybe work for this cam, too?

---

### Post by mips on 2006-08-28
spca5xx v4l1 does NOT currently support your hardware. According to another website Michel Xhaard is working on support for it in v4l2.

Hang in there, maybe you could volunteer to test the code...

[http://www.students.ncl.ac.uk/a.j.mee/blog/index.php/2006/05/10/acer-travelmate-8204wlmi-with-gentoo/](http://www.students.ncl.ac.uk/a.j.mee/blog/index.php/2006/05/10/acer-travelmate-8204wlmi-with-gentoo/)
[http://mxhaard.free.fr/index.html](http://mxhaard.free.fr/index.html)

---

### Post by Belyel on 2006-08-28
Thank you mips for the response.  I did try the new version of spca5xx to no avail, and did more research on ndiswrapper.  Apparently it is only for wireless drivers.  I looked at the website for scpa5xx for a contact where I could volunteer to test the code, but didn't see a link.  Until then, I'll be patient and hope that eventually I can get my laptop 100% working in Ubuntu.

---

### Post by ampop on 2006-09-24
Belyel,
I have the same problem with a acer aspire 5600. Did you solved the problem?

---

### Post by Belyel on 2007-01-15
Good news!  The January 10 build of the newer version of spca5xx is called gspca411x ( I think).  The name isn't important, but the fact that it works with this camera is very important.   The camera works when building gspca for my system, then using both camerama and ekiga.  In camorama, the image adjustments don't work, but in ekiga it shows a beautiful image of my ugly mug.  Good luck, here's the link:  [http://http://mxhaard.free.fr/download.html]("http://http://mxhaard.free.fr/download.html")

---

### Post by ampop on 2007-01-16
> **Belyel said:**
> Good news!  The January 10 build of the newer version of spca5xx is called gspca411x ( I think).  The name isn't important, but the fact that it works with this camera is very important.   The camera works when building gspca for my system, then using both camerama and ekiga.  In camorama, the image adjustments don't work, but in ekiga it shows a beautiful image of my ugly mug.  Good luck, here's the link:  [http://http://mxhaard.free.fr/download.html]("http://http://mxhaard.free.fr/download.html")

Didn't worked with me. Thanks any way.

---

