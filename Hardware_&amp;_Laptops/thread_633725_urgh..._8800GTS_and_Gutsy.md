---
title: "urgh... 8800GTS and Gutsy"
date: 2007-12-06
forum: Hardware &amp; Laptops
---

### Post by Nzer24 on 2007-12-06
I've been running Gutsy for a while now, and it seemed to be working at least okay, until..

I had just started to fool around with the advanced compiz settings, which was a bad idea already because that often would give me crashes, most likely due to the relatively unstable nvidia graphics drivers for my 8800GTS. Then I left, and when I came back, I had to reboot (another little problem... something about usb error -71?), and the compiz settings were still at pretty close to max. 

It went through the loading bar, but then the screen just went black. I rebooted into recovery mode and changed my driver in xorg.conf to "vesa", to at least get the X environment. It worked, but after I reinstalled the normal driver, it went back to it's black screen. I try this a couple more times, until it gives me a popup that says "HAL not loaded". I've been here before, and it's not pretty. So I just decide to pop in the Gutsy LiveCD and backup and reinstall clean. 

Unfortunately, I had originally installed with the Feisty CD, and that was back when the drivers worked correctly. It gives me this totally crazy screen with stretched graphics and dim colors, although it is obviously the Ubuntu desktop. I open a terminal, but soon after the whole thing freezes. I can't change the drivers because of this, and I don't have a Feisty CD anywhere. Any ideas on what to do? I'm fine with reinstalling the system, as long as I backup a few important files. Also, is there any more stable way to run an 8800GTS? It's getting really frustrating.:(

P.S. System specs:
2 GB RAM
Intel DP35DP Motherboard (P35 northbridge, ICH9 southbridge, integrated ethernet that needs a special driver, so no internet during an install)
Intel Core 2 Quad Q6600 Processor
nVidia GeForce 8800GTS Graphics Card
500GB hard drive (with windows dual-boot via GRUB)

---

### Post by mouseboyx on 2007-12-06
6200 TC did this for me kindof

Sometimes the restricted driver manager installs the wrong driver. Try downloading the driver from nvidia's website instead of the one in the repositories.

---

### Post by tgalati4 on 2007-12-06
I set up a similar machine for a client.  His machine has an E6750 (2.66 MHz) with an eVGA 8600 GTS card on an Intel DP35DP board.  My understanding is the 8800 has two GPU cores vs the single 8600 core.  I set up the restricted nVidia driver through envy and tried various compiz effects, which seemed to work fine.  I also ran through all of the 3D screen savers.

I installed Mint Linux (Gutsy-based) in 19 minutes from popping into the disk to surfing the web on a fresh partition.  As this is primarily a Windows gaming machine, Mint is used for troubleshooting when Windows takes a dump.  Of course it took 2 days to install XP Media Center and countless reboots.

I would suggest turning off compiz and running through all of the screen savers first and see if the restricted driver is stable enough to drive the 8800.

Make a backup of your working xorg because there could be other settings that get changed by envy or the nVidia installer that don't get undone when picking "vesa" as safety boot.

Also, I'm running XFCE under Mint, so there may be interplay with Gnome Desktop (gnome-panel) and compiz that's causing weirdness.

Good luck.

---

