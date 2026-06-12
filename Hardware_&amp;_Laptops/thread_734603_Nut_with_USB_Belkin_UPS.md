---
title: "Nut with USB Belkin UPS"
date: 2008-03-24
forum: Hardware &amp; Laptops
---

### Post by ztomic on 2008-03-24
It would be nice if there was a howto on nut. I'll write it if I can figure it out, but I am really having trouble negotiating the Docs for Nut.

I'm trying to set up a Belkin f6c1500-tw-rk using the USB interface with Nut. It appears that the driver listed @ [http://random.networkupstools.org/compat/stable.html](http://random.networkupstools.org/compat/stable.html) should be **usbhid-ups** but the driver is not listed in **/lib/nut**. I have tried several different drivers which include: hidups, newhidups. Other drivers listed on the hardware page are not installed and it's suggested to read the FAQ. I guess the problem is that there are no clear and up-to-date instructions starting with config file to execution. Any help would be greatly appreciated.

---

### Post by rpankn1 on 2008-03-24
If you do write a how to, I would definitely like to see it. I have a Belkin F6C750-AVR and tried installing NUT 2.0 from the respositories in 7.04 and 7.10, and the .deb of 2.2 from the NUT site, and could never get it working.  The documentation was too cryptic to be of any use, and the other how-tos I found by Googling didn't work.  I tried the Linux version of the software included by Belkin with my UPS, but it's for UPSs using a serial cable -- mine only came with a USB cable -- and it uses a very old version of Java.  It's frustrating because when I run the lsusb command, the output shows a device ID number, but the system can't identify the name of the device because it doesn't have a driver to tell it what to do.  

This is the only thing preventing me from using Ubuntu as my main OS because the power grid where I live can be unpredictable -- especially during the summer between the brownouts when everyone's AC is running, the heat causing transformers to short, and severe thunderstorms knocking the power out.  I know it probably sounds paranoid to base my computing around the UPS device, but I already had one computer fried after a power surge and don't want to have that happen again.  I know I can use my UPS as a "dumb" UPS, but I'd rather have the convenience of not having to worry about being away from the computer for more than 10 minutes at a time in case the electricity goes out and having my computer do a hard shut down.  I also don't want to have to go out and buy a new UPS because these things aren't cheap, and got a great deal on the one I have.

One thing I found hopeful, though, was when I tried out Hardy Alpha 6 and installed the nut-hal package, a UPS tab appeared in Gnome Power Manager, but it listed the battery as 0% even though it had a full charge.  I'm guessing the driver installed helps the system 'see' there's a UPS device, but the driver isn't fully compatible with mine, even though NUT's compatibility lists a Belkin model almost exactly like mine, but with a smaller voltage.

---

