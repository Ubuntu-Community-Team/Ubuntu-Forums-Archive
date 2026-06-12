---
title: "Long question - problem with 8800GT and Ubuntu (liveCD problems too)"
date: 2008-04-11
forum: Hardware &amp; Laptops
---

### Post by billdotson on 2008-04-11
I have an 8800GT 512MB video card, and ever since I got it I cannot run Ubuntu.  I cannot run the the Live DVD of 7.10 either.  The card that I had before is a GeForce 7800GT 256MB.  Ubuntu worked fine with it.  As I cannot even run the Live  DVD of Ubuntu I was thinking of putting the 7800GT back in in addition to the 8800GT.  My motherboard is an Asus P5B Deluxe Wifi-AP Edition.  I have an Antec TruePower Trio 550 watt power supply (3 12V rails).  I have a soundblaster audigy PCI sound card, a 250GB 7200RPM hard drive, 5 in 1 media bay, floppy drive, Maxtor 3200 external USB 2.0 300GB hard drive, a DVD/CD burner, 2 120mm LED fans, 3 80mm LED fans, a keyboard, optical mouse and USB bluetooth adapter.  My motherboard has 2 PCIe x16 slots, although the secondary (black) one can only run at 4x speeds (stupid, I know).  

I was thinking that I could put the 7800GT into the black slot, plug the other PCIe x16 power plug (from the PSU) into it and simply go into the BIOS and turn on or off whichever PCIe x16 slot I wanted.  So if I wanted to boot into Ubuntu I would go into the BIOS and disable the slot with the 8800GT in it and move the monitor cable to the 7800GT.  Then I could switch it back if I wanted to play games on XP or Vista.  However, I do not see a way to turn the individual slots on or off in the BIOS.  I assume that if I was able to turn them off that those ports would not use any power, i.e. so that both my videocards would not be drawing power at the same time.  Since I can't enable or disable the individual slots I do not know how I could choose which one videocard I wanted to use (in addition to the obvious fact I would need to move my monitor cable to that one).  

Even then I do not know if my PSU is big enough to support both videos and all of my other hardware.  I used Antec's power supply calculator ([http://extreme.outervision.com/powercalc.jsp](http://extreme.outervision.com/powercalc.jsp)) and entered that I had: 1 7200RPM hard drive, 2 120mm high power fans, 3 80mm high power fans, high-end motherboard desktop, 8800GT 512MB in SLI, sound blaster with front bay, 1 floppy drive, 1 DVD-RW/DVD+RW drive (messed up there I have a DVD/CD drive that can burn both), front card bay reader, fan controller, front bay LCD display, single socket Intel Core 2 Duo E6600, 2 sticks DDR2 RAM (2 1GB sticks), and 3 USB devices that draw power from the system (although the external drive has its own power supply that plugs into AC).  The calculator recommended 380 watts.  If I changed it to having only one videocard it recommended 318 watts.

Any thoughts on my situation other than simply switching the cards when I want to use Ubuntu, i.e. on the subject of having them both and either turning slots off or having both running at the same time.  If I couldn't turn the slots off I thought that I could just unplug the PCIe x16 power cord from the card I did not want to use, but I do not know if it would then try to draw that much power from the motherboard slot and make my motherboard explode or something.

---

### Post by Existentialist on 2008-04-11
Since you have 2 cards available, you could install with the old card, then switch back to the 8800gt after installing ubuntu and the newest nvidia drivers.  Or you could run hardy 8.04 beta which includes these drivers in the restricted drivers.  I have not ran 7.10 since getting my 8800gts (g92), but everything has ran and installed fine with the 8.04 beta.

---

### Post by Victormd on 2008-04-12
I have an 8800 GT as well, and when upgrading cards, ran into a bit or trouble, so I formatted and re-installed ubuntu (in safe graphics mode - wouldn't work otherwise). Once that was done, I used envy to install the drivers for 3D support... If you've tried to install in safe graphics mode, with no luck, you might try installing from the alternative CD...

---

### Post by billdotson on 2008-04-13
problems fixed.  DVD was bad.  Used a different liveDVD in safe graphics and installed, then "sudo apt-get install build-essential", "sudo /etc/init.d/?dm stop" (to stop gdm/X) and then installed the nvidia driver downloaded from their website.  Of course you have to remember to have it downloaded and have it in a place you can find before you kill X.

---

### Post by SynthesizersFTW on 2008-04-15
Bill,

I know from reading reviews before I got my 8800GT that the card's draw under a heavy load can be over 200W by itself, just FYI - I don't know if you're going to push it hard, but be prepared.  I think I read this at [www.beyond3d.com](www.beyond3d.com), not sure anymore.

Cheers

---

