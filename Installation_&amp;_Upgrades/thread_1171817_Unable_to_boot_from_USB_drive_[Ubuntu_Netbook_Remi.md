---
title: "Unable to boot from USB drive [Ubuntu Netbook Remix] on Asus EEE 900a netbook-Xandros"
date: 2009-05-27
forum: Installation &amp; Upgrades
---

### Post by fuwkej on 2009-05-27
I am trying to change a new netbook's operating system from Xandros (It's a bit too simple) to Ubuntu netbook remix. I have the USB stick (Lexar) already made up using the direct link from Ubuntu's website iso, and using the automatic usb writer in Ubuntu. The USB is recognized when Xandros is operating, but the Asus EEEPC 900a netbook does not recognize it when attempting to boot to it. Modified BIOS settings for device to boot, but no combinations worked. Attempted to load via hitting ESC, but the only option available was the 4GB SSD HD.

Xandros actually works better than I thought it would, with big fonts and links suitable for a netbook - but it's not very customizable. 

Any help is appreciated.

---

### Post by linesma on 2009-05-27
I have a EEE 900HA and installed Ubuntu from a USB flash drive.  I found I had to 2 things to get it to work. 1. Change the boot priority in the bios to have the USB flash drive as the primary device.  I also had to ensure that the USB drive was plugged into my machine both during changing my bios settings, and while I booted the machine.

Let me know if this helps.

linesma

---

### Post by fuwkej on 2009-05-31
I had the wrong filesystem on my flash drive, changed it to reiserfs and it loaded great. thanks

---

### Post by Hehehehehe on 2010-12-07
Hi, I am really really new at this so please excuse my silly question. 

How do I change the systemfile on the USB stick? I am having the identical problem. There were no errors at writing the boot file onto the stick, but somehow the computer flat out refuse to boot from the USB. 

Thanks!

---

### Post by wilee-nilee on 2010-12-07
> **Hehehehehe said:**
> Hi, I am really really new at this so please excuse my silly question. 

How do I change the systemfile on the USB stick? I am having the identical problem. There were no errors at writing the boot file onto the stick, but somehow the computer flat out refuse to boot from the USB. 

Thanks!

Look on Google with your computer model and per-session boot.

There is a key prompt like getting to the bios that will bring up a boot from menu outside of the bios mine is f12 the eeepc is esc.

---

