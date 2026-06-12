---
title: "USB IDE HDD not noticed in Ubuntu"
date: 2008-04-22
forum: Hardware
---

### Post by LeoSolaris on 2008-04-22
I bought a case for my old HDD from my previous laptop. I just got it today, plugged it all in, light came on, and that was that. No mention of it on any of the USB ports in /media/ just a light and I can head the HDD spin.

Here is what I get for lsusb
03:55:13 on Tue Apr 22 - leo:~$lsusb
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 007 Device 008: ID 14cd:6600  
Bus 007 Device 004: ID 05a9:2640 OmniVision Technologies, Inc. 
Bus 007 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 006 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  
Bus 005 Device 004: ID 046d:c521 Logitech, Inc. 
Bus 005 Device 001: ID 0000:0000  

The device 8 is apparently the HDD, but I am at a loss after that.

I restarted and went to XP. I got a step farther at least. Plugged it in, XP recognized it said it was a mass storage IDE device, and it was ready to be used. I thought I had it made till I went to my computer, where the device should be listed, and it wasn't there. There was still a little icon on my status bar that let me 'safely disconnect the USB device' but no device!

I am a little frustrated at this one. I need to get some of the files that are on that old hard drive, including a half finished novel I have been working on.

Any help would be greatly appreciated!

Leo

Alright. I have played with this thing for a while now, and I think I know what went wrong. IBM used a proprietary HDD in the Thinkpad A30. I haven't been able to completely confirm this, but it's the only reason I can think to explain the extra 4 prongs and the missing prong on the bottom row near the middle. I have hunted through Google but nothing about the hard drived used in the A30 say if they are proprietary or not.

I think I will write this one off and just buy one with my tax refund when it gets here.

Thank ya anyways!

---

### Post by lauriejb on 2008-04-23
USB isn't always universal unfortunately, and it sounds as if someone hasn't done their design properly.  You might pull the thing apart and remake all the connections again.  Occasionally when stuffing the wires into the case they shift the connections.  Worth a try.

---

