---
title: "External monitor 2405FPW with Latitude X1, Feisty Fawn (modesetting)"
date: 2007-01-21
forum: Hardware &amp; Laptops
---

### Post by Bjoern on 2007-01-21
Hello,

I can't seem to get the external monitor (Dell 2405FPW) to display the 1920x1200 resolution. I guess my problems already start with not being exactly sure how to configure an external monitor. Can anybody help?

I have installed Feisty Fawn (7.04) and installed the modesetting driver package (as 915resolution didn't work with my 2405FPW).

However, with the attached xorg.conf it only starts X in clone mode, and the 2405FPW also only shows the 1280x768 resolution.

If I change the BusID for external screen to 0:2:0 startx fails.

Is the problem in the line 

> (II) Primary Device is: PCI 00:02:0
(WW) I810: No matching Device section for instance (BusID PCI:0:2:1) found

in the Xorg.0.log? What does it mean?

Many thanks in advance for any help!


Bjoern

---

### Post by JohnPhys on 2007-01-21
This looks like a known issue with the intel series of graphics chips/drivers (not sure exactly where the fault lies).  They don't seem to natively support the widescreen resolutions.  You need to install 915resolution and follow the instructions here

[http://easylinux.info/wiki/Ubuntu:Edgy#How_to_Correct_the_Graphics_Resolution_.28Intel.29](http://easylinux.info/wiki/Ubuntu:Edgy#How_to_Correct_the_Graphics_Resolution_.28Intel.29)

Good luck!

EDIT:  I should add that I've only done this to get the attached laptop to display correctly (and not on a dell).  Getting the external monitor to display correctly may take some more digging.

---

### Post by Bjoern on 2007-01-23
Thanks, but I don't think that is the solution. I could be wrong, but I thought the "modesetting driver" for the intel chipset is meant to replace 915resolution. My experiments with 915resolution were unsuccessful, presumably because it couldn't set the creen refresh rate precisely enough. Modesetting driver was supposed to change that, as it doesn't rely on the settings available in the BIOS.

Any other ideas? Any xorg.conf for an external monitor out there (would be a start, as at the moment I can't even get it to run anything but clone mode, let alone the desired screen resolution).

---

### Post by foobardude on 2007-02-06
Were you able to get this working?  I'm in the same boat as you, but I'm using the i810 drivers for now.  If you have a good modeline for the dell monitor, let me know.  I'm on a i945 chipset with the 1920x1080 working, but no dice on the 1920x1200... seems silly...

---

### Post by foobardude on 2007-02-28
OK.. got it working... the problem was the modeline.  Here's the settings:

        ModeLine "1920x1200"  154  1920 1968 2000 2080  1200 1203 1209 1235 +hsync -vsync


Should work like a charm.  By the way, don't bother with the dual monitors at this high of settings - the chip isn't made for that much power.

---

