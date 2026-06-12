---
title: "&quot;Boot Error&quot; when trying to boot from 8.10 bootable thumb drive"
date: 2008-12-14
forum: Installation &amp; Upgrades
---

### Post by ratdog on 2008-12-14
Hello,
I'm trying to install Ubuntu 8.10 on an older windows system with no CDROM drive.
I've used the "Create a USB startup disk" app in Intrepid to create a bootable 1G thumb drive.
I have setup the BIOS on the old system to boot from USB (it gives me 2 usb options:USB FDD and USB ZIP, I have tried them both with the same results).
When I try to boot from the thumb drive it gets past the system tests and just says "Boot error"
The old system had an ASUS A7V8X-X motherboard with a BIOS from 2003.  Is this system too old?  I'm confused because it does give me the option to boot from USB in the BIOS.
Any info greatly appreciated.

---

### Post by logos34 on 2008-12-14
does the machine have an OS installed? windows, another linux?

Edit: nm, you said 'older windows system', duh

Try this guide:

[https://help.ubuntu.com/community/Installation/FromWindows](https://help.ubuntu.com/community/Installation/FromWindows)
('CD image approach' or automatic)

---

### Post by ratdog on 2008-12-14
Yeah, it has Windows 2000 installed.  I can access the USB drive from within windows and run the Ubuntu installer, but to do a fresh install the only way I see is to boot from the disk.  Is there another way?  I want windows off of there completely!
Thanks

---

### Post by logos34 on 2008-12-14
if you decide to use the cd image approach and have any questions, let me know. Haven't tried it in around a year but it used to work great

---

### Post by ratdog on 2008-12-14
Cool, I will try UNetbootin.

---

### Post by ratdog on 2008-12-14
UNetbootin didn't work for me  :(

I used an .iso I already downloaded and installed to another machine just fine.  When I rebooted to the Ubuntu installer, I got some error like "ATA2: link is slow to respond, please be patient."  then "ATA2: SRST FAILED"

There is also another error when scanning scsi drives.
"Driver 'sd' needs updating - please use bus_type methods"
Does this mean I need to update the BIOS?

Does anyone have any other idea for how to install from the thumb drive.
I'm about to throw this old machine in the dumpster!

---

### Post by logos34 on 2008-12-14
> **ratdog said:**
>  "ATA2: link is slow to respond, please be patient."  then "ATA2: SRST FAILED"

found this over at launchpad:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/220706](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/220706)

might want to search there for info on the other message.

maybe try the cd image approach but its possible you'll end up with same errors

---

### Post by ratdog on 2008-12-14
I actually did try it from the cd image because there is no internet access where that computer is right now.

---

