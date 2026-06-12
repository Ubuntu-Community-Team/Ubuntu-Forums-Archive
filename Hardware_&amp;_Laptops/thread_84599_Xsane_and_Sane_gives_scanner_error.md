---
title: "Xsane and Sane gives scanner error"
date: 2005-10-31
forum: Hardware &amp; Laptops
---

### Post by GrootBrak on 2005-10-31
After upgrading to breezy, my scanner won't work. Neither Xsane nor Sane wants to see it. I reinstalled both aps just to make sure.

The error I get is "failed to open device snapscan libusb:004:003: Invalid argument."

Here is my output from lsusb:

> jacques@HomePC:~ $ lsusb
Bus 008 Device 001: ID 0000:0000
Bus 007 Device 001: ID 0000:0000
Bus 006 Device 001: ID 0000:0000
Bus 005 Device 001: ID 0000:0000
Bus 004 Device 003: ID 04a5:20b0 Acer Peripherals Inc. (now BenQ Corp.) S2W 3300U/4300U
Bus 004 Device 002: ID 0a12:0001 Cambridge Silicon Radio, Ltd Bluetooth Dongle (HCI mode)
Bus 004 Device 001: ID 0000:0000
Bus 003 Device 004: ID 04b8:0005 Seiko Epson Corp. Stylus Printer
Bus 003 Device 001: ID 0000:0000
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 001: ID 0000:0000

My scanner is the "Acer" bit.

Also in Synaptic when I click on repositories, nothing happens. Is that a problem with the new synaptic?

---

### Post by rsay on 2005-11-01
I'm having the same problem. Things were working well in hoary and then seemed to get messed up after the dist-upgrade to breezy. For a while, I could run xsane as root but now that gives me the same error. I found a bug on bugzilla that sounded similar but I couldn't figure out what to do. 

[https://bugzilla.ubuntu.com/show_bug.cgi?id=16232]("https://bugzilla.ubuntu.com/show_bug.cgi?id=16232")

Let me know if you have any luck

---

### Post by GrootBrak on 2005-11-10
No luck so far. After upgrading breezy again, I notice now some other errors complaining that I should try and run sane as root. I will try that and go through the fix on the Xsane website. I saw the Xsane fix quoted somewhere on Ubuntuforums verbatim, but can't find it now. At the time my fault was unrelated to the fix. But right now it might just work.

---

### Post by Bartje on 2007-02-02
How do I get my scanner working?

I get the error message snapscan:001:006
Error during communication with device (translated to English, because my system is in Dutch)

these are my usb connections according to lsusb
bart@bart-desktop:~$ lsusb
Bus 007 Device 003: ID 058f:6362 Alcor Micro Corp. 
Bus 007 Device 001: ID 0000:0000  
Bus 006 Device 003: ID 04b4:6830 Cypress Semiconductor Corp. USB-2.0 IDE Adapter
Bus 006 Device 002: ID 0781:5151 SanDisk Corp. Cruzer Micro 256/512MB Flash Drive
Bus 006 Device 001: ID 0000:0000  
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 002: ID 056a:0060 Wacom Co., Ltd 
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 005: ID 04a5:20de Acer Peripherals Inc. (now BenQ Corp.) S2W 4300U+
Bus 001 Device 001: ID 0000:0000  

My wacom doesn't work either... I'm getting really frustrated about this so called 'user friendly Ubuntu'...

I get no responses on my questions either!i

I switched to Ubuntu, because it worked with my 965G chipset, and Suse didn't.
It did work on my previous computer, and my scanner, and my wacom did work with some simple clicks using 'Yast'. In this so called 'user friendlyness' of Ubuntu I do nothing much more then changing .conf files, and get no work done at all!!!!!!!!!

If I don't get it working soon, I'll try to find a workaround to get Suse on this PC anyway. I have no choice.

---

### Post by alienexplorers on 2007-02-06
Try loading libsane and libsane-extras from synaptic.  My scanner will not run with just sane and xsane without these files loaded.

---

### Post by MeduZa on 2007-02-16
You need to create a link to your scanner backport for xsane, sane have the backport on /usr/lib/sane/ and xsane on /usr/local/lib/sane/ you need to make links from /usr/lib/sane/ to /usr/local/lib/sane/ for your backport files .so and .so.1 

good luck

---

### Post by Arkore on 2007-06-22
I have this exact problem and have tried various combinations of sane, xsane and lib-sane ect... but so far nothing works.

Forgive me for being an ignorant windows user that has just changed to ubuntu but how does one create a link between these different files?  I don't understand what I need to do to try this out.

I also came across a few people saying I have to mount my usb scanner to make it work and set read/write privileges, can anyone give me some ideas on this?

---

