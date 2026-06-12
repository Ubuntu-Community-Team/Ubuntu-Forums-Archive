---
title: "Locks up on boot since ndiswrapper"
date: 2005-10-15
forum: Hardware &amp; Laptops
---

### Post by wizzzer on 2005-10-15
Dell laptop locks up on boot since installing ndiswrapper with either Wifi card or Ethernet card in PCMCIA slots.  I have to remove the battery and pull the plug to shut down.  If I boot WITHOUT either card in it, it boots OK.  Cards will work as they should, if they are put in AFTER boot.  It seems to lock up at "Starting hotplug subsystem" every time, if either card is in a slot.  Any ideas?  I'm new to Linux and am impressed with Ubuntu so far.  If I get this to work smoothly, I'll be a convert.  That's saying something after working over 30 yrs in a DOS/Win environment. 
Cheers, Wizzzer

---

### Post by wizzzer on 2005-10-15
For some unknown reason. It stopped locking up.  I wish I knew what did (or undid) it, because I have another machine just like it that I would like to do.  Since it belongs to my wife and I'd rather not have to go a few rounds with her, I'd like to know what caused it.  (She's little but snake mean).  PLEASE don't tell me it was re-booting, it took 3 re-boots before it finally worked.  I have an extra HD, guess I'll be safe and do her's that way.   Cheers, Wizzzer

---

### Post by wizzzer on 2005-10-15
I guess it was just a fluke.  It booted fully twice, I re-booted again, repeatedly, and we're back to the lock up.  If I take the card out (either) it boots fine.  Otherwise, it's still locking when it displays "Starting hotplug subsystem".  Is there some way to disable the ndiswrapper during boot?  Everything seemed to be working fine until I did the ndiswrapper -m (following their instructions) to add it to the boot process.  They didn't tell you how to undo it.  Any help would be appreciated.... 
Thanks, Wizzzer

---

### Post by az on 2005-10-15
Sometimes, a wireless card's driver needs to load firmware to initialise itself.  Perhaps your was having trouble with this...  I know a few usb wireless devices that need to be plugged and unplugged the first time they are used on a certain machine, and then they work forever and ever....

Pulling your hair out is a rite of passage into wireless.  It is OS independant.

---

### Post by feratson on 2005-11-08
I have a Dell D610 and had the same problem.  Here is what I found when you plug the laptop into ac power it will boot up just fine but when it is not pluged in it will lock up.  It turns out that if you go into the bios and change the boot option to "Thorough" boot you will no longer have this problem

---

### Post by mavr on 2006-11-11
i've got the same exact problem but on a different laptop so i can't believe it's just a problem of your machine's bios. I guess there is something wrong in the hotplug system or in the ndiswrapper module, but i know nothing about this things and i really don't understand while it works plugging the card after boot and it doesn't if i boot with the card in. Maybe and upgrade will fix this one day :(

---

