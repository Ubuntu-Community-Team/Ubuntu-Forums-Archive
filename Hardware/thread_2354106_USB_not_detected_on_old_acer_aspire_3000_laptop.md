---
title: "USB not detected on old acer aspire 3000 laptop"
date: 2017-02-28
forum: Hardware
---

### Post by dumble on 2017-02-28
I am trying to install ubuntu 14.04.5 on an old laptop of a friend. Its an acer aspire 3000, this thing still got a floppy drive and makes more noise then my lawnmower. 

Currently its still with windowsXP and its not working properly anymore. I figured just put my linux-usb in and install ubuntu and see if we can still be able to use it a little. But then encounterd a problem, the usb is not listed in boot menu (f12). Tried the fowling things:
- Boot computer, leave usb in untill detected in windows, reboot
- Shutdown with usb, boot
- Shutdown, boot, quickly put usb in when screen turns on, press f12
- Tried all 3 usb ports
- Updated bios from 3A31 to latest 3A32
- Tried all of the above again
- Quiet boot enabled/disabled in bios


Weird thing, when you disable quiet boot, and you boot with usb plugged in, it is listed. You see that its loading all the hardware, and my usb kingston device is there. But then I press F12 and I only get options:
* hard drive
* cd rom
* floppy
* boot on lan

So before I go the store and get a cd I was wondering if there is anything else I could try.. 

*also the laptop does not have a battery anymore, so it always needs to be plugged in...

---

### Post by mörgæs on 2017-02-28
Ubuntu is too much of a workload for an Aspire 3000. I suggest that you try Lubuntu 16.04.2.

---

### Post by Autodave on 2017-02-28
I agree w/morgaes: you want Lubuntu on that machine.

You kinda answered your own question when you stated that USB is not listed in the boot menu. Since it isn't listed, you will never be able to boot from it. You will have to get that burned to a DVD disc an an .iso file and boot from that.

---

### Post by RobGoss on 2017-02-28
+1 Autodave

---

### Post by thesolitarylodger on 2017-03-26
I know this thread is a little old, but for anyone trying to boot from USB for an older Acer 3000:

It's extremely easy to miss, but in the Boot menu in BIOS, you may need to hit enter on HDD first; it then should give a submenu, which then should list the USB and the HDD (where you can then change the boot order).   I was able to boot on an Acer Aspire 3002lci with no problems.

However, the overall performance will definitely be a downgrade, as this older system can't handle as much.

---

