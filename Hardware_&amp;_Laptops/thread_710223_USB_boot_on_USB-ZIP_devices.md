---
title: "USB boot on USB-ZIP devices"
date: 2008-02-28
forum: Hardware &amp; Laptops
---

### Post by mgaedwards on 2008-02-28
Hey first post to this board. Old Unix salt though. So pardon me if I get parts wrong.

The purpose of the post is just clarify the article :

[http://www.pendrivelinux.com/2007/09/28/usb-ubuntu-710-gutsy-gibbon-install/](http://www.pendrivelinux.com/2007/09/28/usb-ubuntu-710-gutsy-gibbon-install/)

and save those with a USB-ZIP flash drive many many hours of time.

Excellent article. Kudos to the author. Note that the article only addresses USB-HDD drives. 

Note that a USB flash is a USB flash, and the motherboard bios or something determines what the USB flash comes up as. Luckily I have more than one machine otherwise I would have pulled my hair out. 

First the USB-ZIP issue:

1. The boot parittion with Ubuntu 7.10 has to be partition 4. /dev/sd4 in my case. I found this in another article on the web, but the build must have been old so it didn't quite work. So follow pendrives instructions and when he says to make partition 1, make 4. This is the magic.
 
2. Follow the rest of the instruction, making the fat on /dev/sd4. Almost forgot, it is important to remove and re-insert the usb. When you do this it automagically creates the /dev/sda4 in the /dev directory. In the old days this automagic didn't exist and you had to run MAKEDEV on the device by hand. For a live CDROM that would be a problem.

You also may have to run lilo again if you were playing around and somehow trashed it. I think that is all that is to it. It WORKs!

Lastly,

 on USB-HDD boots, the newer motherboards or bios has a boot priority in addition to the 1st boot, 2nd boot setting. Setting the priority to the USB-HDD drive works until you remove and boot again. Booting without the USB takes it out of the priority and you must go back in to set the boot priority back to the USB or it will boot to the hard disk. Kinda screwy but that is the way it works.

FYI  I bought a AMD AM2 Sempron, a cheap AM2 Jetway motherboard, and 1 gig of ddr2 -800 ram (wintech or something like that). a couple of usb drives, with shipping for about $145. Slapped the stuff into an old computer case with a power supply (board has an 8 pin 12volt input jack, but slapping a 4pin 12v jack to the right side works fine ) .

Linux rocks!

mark

---

