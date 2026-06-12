---
title: "USB digital picture frame support"
date: 2008-04-14
forum: Hardware &amp; Laptops
---

### Post by raydar on 2008-04-14
I've been trying to get a Pandigital PAN56-1 digital picture frame to work properly under Ubuntu Gutsy.  It's a USB device with internal memory as well as a slot for a flash memory card.

When I first connect the picture frame to the computer with a USB cable and switch the picture frame's power on, the connection is noticed by both the computer and the picture frame.  If I'm quick, I can open a Nautilus folder for the picture frame and browse the sample files loaded by the manufacturer into the picture frame's memory.  

But after about a minute, the connection is lost, and the picture frame no longer shows up as a mounted device.  When I either turn the picture frame's power off and back on or unplug and re-plug the USB cable, the picture frame notices the connection, but the computer does not react except in the hardware information, where the device disappears and reappears accordingly (see attached screenshots).  Only restarting the computer lets me get the picture frame back as a mounted device for the brief time described above.

I'm still new enough to Linux hardware manipulation that I'm pretty sure some other USB device is just overriding the picture frame and that there's something I can specify in a config file to make everything play nice--but I don't know how to go about it.  The computer has 2 USB slots, one with a mouse plugged into it and the other with, usually, a printer plugged into it; I have to unplug the printer to use the picture frame, because although the printer has an extra USB jack, the picture frame won't connect if it's plugged into that one (not a powered jack, or something?).  

Could CUPS (not that I know how it works) be expecting the USB printer to be present and, when it doesn't find it, be interfering with the connection to or mounting of the picture frame?  Maybe I just need to find an old PCI USB port card, to provide a whole 'nother route for mounting USB devices?  

Thanks for any insight & help!

---

### Post by teaker1s on 2008-04-15
while I don't know the exact solution to your issue, I would like to suggest two things
1) on desktop panel,right click and select add to panel, select disk mounter.
2) have you tried a mains power adapter for the frame? it's possible it power saves.

Regards

Dan

---

