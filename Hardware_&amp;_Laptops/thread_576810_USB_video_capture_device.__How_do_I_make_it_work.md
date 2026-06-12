---
title: "USB video capture device.  How do I make it work?"
date: 2007-10-15
forum: Hardware &amp; Laptops
---

### Post by Darkgnat on 2007-10-15
Hi.  I'm not sure if what I want to do is even possible, so maybe someone could either point me in the right direction or tell me that it's not gonna work.

I have recently come into the possession of a USB 2.0 s-video video capture device calling itself "EasyCAP".  It's intended for Windows and it comes bundled with some Windows video editing software.  I was hoping that I would just be able to use it as an s-video input for my computer so that I could watch whatever I inputed into it in TV Time or some such program i.e. make it appear as /dev/video0 or something.

I don't know if the device has any Linux support, but it now appears in device manager under "USB 2.0 video capure device" as "USB Vendor Specific Interface" and shows the vendor as "Syntek Semiconductor".  There's also lots of other information that I could probably get in the command line if I knew the appropriate command.  Basically I don't know how to proceed.  This web page ([here]("http://hardware4linux.info/component/17354/")) seems to suggest that usb_stk11xx_driver might be a relevant module, but I don't know what to do with this information.

Sorry for not knowing what I'm talking about more.

Thanks

---

### Post by Hugh Mulqueen on 2008-01-10
Hi
I have the EasyCap USB thing and i have been trying to get the drivers and software for a month and a half.

I have come up with software that might work, unicap which you can get at:

[http://www.unicap-imaging.org/download.htm](http://www.unicap-imaging.org/download.htm)

and camorama to test it, which can be got with apt-get:

sudo apt-get install camorama

Now as for drivers, the best one I could come up with was a driver for a web cam called stk11xx-1.2.3. it might work with your machine. Check it out anyway. heres the address:

[http://sourceforge.net/project/showf...roup_id=178178](http://sourceforge.net/project/showf...roup_id=178178)

Get the tarball and extract it. read the readme file.
And pray that it works.

There is a tutorial on how to install the driver in ubuntu forums:

[http://ubuntuforums.org/showthread.p...+Semiconductor](http://ubuntuforums.org/showthread.p...+Semiconductor)

Hope this helps, Let me know how you got on!

Good Luck!!!

---

