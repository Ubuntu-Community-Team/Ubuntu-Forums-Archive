---
title: "Dell Inspiron 8000 w/Dell 7345U docking station problem"
date: 2006-01-02
forum: Hardware &amp; Laptops
---

### Post by doctoryes on 2006-01-02
I have a Dell Inspiron 8000 laptop for which I've recently bought a Dell 7345U Port Replicator/Docking Station. I have an existing install of Windows XP that I'd like to get rid of in favor of Ubuntu's Breezy release. I'm using a Breezy i386 Live CD to make sure that all my hardware is supported before wiping the hard drive and installing.

When I boot the Breezy Live CD, it boots fine when not docked - the display and everything else works fine. However, when docked, the screen blanks out when X is supposed to start (both the LCD and the monitor which I have connected via the docking station). Here's the things I've tried:
- Booting using:
    - "live vga=771"
    - "live vga=775"
    - "live vga=771 noapic nolapic"
- Booting using a Knoppix 3.9 Live CD - same issue when starting X.
- Booting WinXP while docked - display shows up fine on both LCD and attached monitor. :mad: 

I've attached the /etc/X11/xorg.conf file that is automatically generated - maybe it'll help shed some light. I've tried changing the driver from "ati" to "r128" and doing a "sudo /etc/init.d/restart gdm" and it still didn't fix things. I also tried restarting gdm after changing the weird "1400x1050" resolution to "1280x1024" and it still didn't display anything. 

I'd be more than willing to post any other info also.

Ctrl+Alt+F{1-6} worked fine to get a viewable terminal when the display wasn't displaying otherwise.

Specs:
Dell Inspiron 8000 docked to Dell 7345U
192 MB RAM
Pentium III 700 MHz
ATI Mobility M4 display adapter

Thanks!

---

### Post by doctoryes on 2006-01-05
OK, I see I've gotten no bites so far...

I'm going to experiment more with this issue (when I have the time), but in the meantime, please reply to this post if you've had the same problem with this docking station.

Thanks!

---

### Post by Bytebull on 2006-01-05
Theres a new bios firmware update for that version that has fixes for the docking station. I breifly ran accross it at the dell site one day....

not much more I can give you. Check at the site and I bet you find the new bios that will fix your docking problem.

---

### Post by doctoryes on 2006-01-08
OK, here's where I am on this:

I upgraded my laptop's BIOS from A21 to A23 using the upgrade on Dell's website. However, Ubuntu 5.10 Live CD still didn't display anything after starting X. So I tried Knoppix 3.9 again to see if it worked. At first, it didn't but then I found that I could use the "fb800x600" kernel parameter which made Knoppix use a driver named "fbdev" which I assume uses frame buffer graphics without using hardware-acceleration specific to my graphics card. And, viola, X showed up fine on my laptop display and the monitor which I have connected via the port replicator.

So, is there a way to bypass hardware acceleration and use a frame buffer driver with an Ubuntu Live CD? When I use "vga=771" or some other VGA number, it still attempts to use the "ati" driver which doesn't work.

And also, is it the "ati" driver that's the problem here? It seems like that to me, but I'm no X-pert.

Any info would be appreciated. Thanks, bytebull, for your response.

---

### Post by doctoryes on 2006-01-09
BTW, can someone tell me which ATI driver version is included in Ubuntu 5.10? How can you tell the version of a specific driver in general?

I want to try the most recent version of the ATI driver from ATI's website, but I'm having trouble doing that from a Live CD boot and I'd like to know whether or not Ubuntu already uses the most recent driver.

Thanks!

---

