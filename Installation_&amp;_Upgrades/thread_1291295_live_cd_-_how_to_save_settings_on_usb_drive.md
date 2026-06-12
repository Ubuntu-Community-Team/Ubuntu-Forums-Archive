---
title: "live cd - how to save settings on usb drive?"
date: 2009-10-14
forum: Installation &amp; Upgrades
---

### Post by oldram on 2009-10-14
[SIZE=3]I want to run ubuntu from the live-cd.  
How do I have all the configuration settings placed on a USB drive so they will be used in future boots?[/SIZE]

---

### Post by junke1990 on 2009-10-14
with the standard live cd/usb it isn't possible, it loads the files from the usb to the memory and afterwords just unload it without the writing. because you put a cd image on an usb, on a cd it isn't possible to write to. 

I dont know if there is a special build for it but you can try to install  it to your usb but this wil give you a lot of problems.

where do you wanna use it for?

---

### Post by raymondh on 2009-10-14
You might want to consider a "persistent" USB.

[https://wiki.ubuntu.com/LiveUsbPendrivePersistent](https://wiki.ubuntu.com/LiveUsbPendrivePersistent)

Regards,

---

### Post by Mighty_Joe on 2009-10-14
> **junke1990 said:**
> with the standard live cd/usb it isn't possible, it loads the files from the usb to the memory and afterwords just unload it without the writing. because you put a cd image on an usb, on a cd it isn't possible to write to. 


You are misinformed.  The [Live USB Creator]("http://en.wikipedia.org/wiki/Ubuntu_Live_USB_creator") on the Live CD can create a persistent partition that will save one's changes.  It is also possible to use the Live CD in tandem with a USB drive to [save one's settings on the USB drive]("https://help.ubuntu.com/community/LiveCD/Persistence").

---

