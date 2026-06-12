---
title: "Can I upgrade my BIOS with Ubuntu"
date: 2008-04-07
forum: Hardware &amp; Laptops
---

### Post by markcgriffiths on 2008-04-07
Hi,

I want to download this, it will fix a problem with the fan so that it will run quieter.  Is it possible with Ubuntu as it's a Windows exe?

[Driver]("http://h10025.www1.hp.com/ewfrf/wc/softwareDownloadIndex?softwareitem=hb-14718-1&lc=en&cc=us&dlc=en&product=385154&os=181&lang=en")

---

### Post by MiataMuc on 2008-04-07
No, this doesn't work. But there seems to be a bios-update on a bootable disk, which should work (as long as you have a floppy disk drive).

Flo

---

### Post by felker2 on 2008-04-07
I can upgrade my BIOS of my Asus M2A-VM HDMI without using an OSl: put the new BIOS image on a USB stick, reboot the system, go into the BIOS and select to upgrade the BIOS image from the USB stick.

That's it.

---

### Post by ljonesj on 2008-04-07
not all laptops and desktops can do this yet but i like the idea of this update with a usb stick can you still boot into windows or are you all ubuntu on the machine

---

### Post by TenPlus1 on 2008-04-07
Maybe running this file through WINE will allow it to run, unpack and create the much needed floppy-disk for your Bios update...

also, a quick VirtualBox install with WinXP will allow you to run it also, and lastly, find a friend with Windows and use their Pc for 5 minutes to do the same...

---

### Post by felker2 on 2008-04-07
If your BIOS does not support upgrading itself, you could try a live-Windows-boot from CD (see [http://en.wikipedia.org/wiki/BartPE](http://en.wikipedia.org/wiki/BartPE)), and from there run the Windows-only BIOS-upgrade-program.

---

