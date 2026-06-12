---
title: "All in One Scanner"
date: 2004-11-03
forum: Hardware &amp; Laptops
---

### Post by mattyh on 2004-11-03
Okay, I had a thread started earlier on getting printing to work for my hp psc 2110, but now that works, so I need to get the scanner to work, but xsane says there are no devices found.  Has anybody set an hp all in one up under ubuntu or any other linux?  It was autodetected in Mandrake 10.1 a while back, so I know it should work in linux, I just have no experience setting it up manually.

---

### Post by Allen S on 2004-11-04
I have a PSC-750 that I was able to get working under Ubuntu

In the universe repository there is HPJO which are the ptal drivers for the HP PSC seris printers and most of the HP all in one printers. Install it and during the install it will ask if you want to scan the parallel port you can answer no to this one. Next it will ask if you want to scan the USB bus answer yes. Chose the defaults for the rest. At this point my sanner worked but not the printer. I hadn't installed it yet. If both your now work you are good to go. If not delete the printer and add it back in the normal way.
For some reason I could not print after I did a cold reboot and then installed the printer.

I just did a clean install because I added a HD and this time I added some things that required the KDE libs before I added the printer and I had some problems getting the scanner and the printer to both work. When I was testing Ubuntu I got the PSC-750 tp work without much problems.

I'm also using the AMD64 version so I don't know if that makes a difference. I've read where it still has a few problems and is not quite up to par with the x386 version.

Allen

---

### Post by mattyh on 2004-11-04
Thanks for the reply, I actually already installed hpoj, and I had done all that you are talking about, but the scanner doesn't want to be recognized unfortunately.  I had weird issues w/ getting the printer to be noticed, too.  It finally worked after I unplugged and replugged the usb cord in while ubuntu was running, then installed the printer again, and that time it actually would print, whereas before it would just queue it.  My external hard drive is the same way when it comes to being noticed.  If I boot up w/ it on it doesn't automount, but if I turn the switch on and off it shows up on my desktop.  Seems like there is some sort of bug in the hardware detection or something.

---

### Post by Allen S on 2004-11-05
For what ever reason after installing the printer/scanner driver using ptal-init the scanner would work but not the printer. If memory serves me right in the printer config it showed up as a PSC-700 series. After rebooting it the also showed the PSC-750 and I was then able to install the printer and print a test page.

I'm having the same probem as you with my USB HD. Sometimes it will work and sometimes not. Not sure what that is all about.

I hope that they get the USB hotplug of stoage device straightened out. I really like this distro. 

I know it can be done, I have Xandros installed on another computer and the usb hd, memory stick, & card reader all work, you can hot plug them or they can be plugged in during boot. The printer was amazing, I configured the printer through the control pannel and the scanner worked. It's a nice distro but I don't like the fact that you can only install packages that are optimized for it.

---

