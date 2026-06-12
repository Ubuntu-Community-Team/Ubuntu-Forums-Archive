---
title: "Boot issue USB HDD"
date: 2009-07-05
forum: Installation &amp; Upgrades
---

### Post by kasper22 on 2009-07-05
Hi Guys,

I've installed Ubuntu 9.04 onto a external USB hdd that I have.  To install I did a normal install, and then once finished setup grub as a MBR on the external drive.  

Now I can plug in the drive and boot from it, mostly.  The problem I'm having is that the boot process starts and goes a little while then fails with a message stating that it can't find the uuid that it is suppose to boot from and I end up in busy box.

To get around this I just disconnect the drive and plug it back it.  It gets recognized as a drive and then I exit busy box.  Then everything is find from that point on.  So it seems like the problem is the boot image doesn't scan the usb drives before it tries loading the driver modules.

So the question is, first does that sound right and if yes, what do I need to do to make sure the usb drives are scaned before the modules try to load?

Thanks
Bryan

---

