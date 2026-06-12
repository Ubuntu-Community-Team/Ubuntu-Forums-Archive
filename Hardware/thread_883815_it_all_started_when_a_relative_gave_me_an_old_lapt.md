---
title: "it all started when a relative gave me an old laptop..."
date: 2008-08-08
forum: Hardware
---

### Post by BetterSense on 2008-08-08
Some old IBM business laptop with 128mb ram, docking station, external CD drive and all. I thought, hey, it would be great to make a digital picture frame out of it. I've always wanted one of those. Should take, like, one evening. But as usual, the planets have really aligned to make his project impossible for me.

First of all, the HDD sounds like a rattlesnake orgy, so there's no way I can use a conventional install. It would be too loud. I honestly don't know how it's possible to make a 2.5 inch hard drive this loud without it self-destructing.

Cool, I'll just go into the BIOS power saving options and tell it to sleep the hard drive as much as possible. Surely it won't need to spin the HDD when playing a picture slideshow. O wait, the BIOS power saving options won't allow HDD sleeping when on AC power.

Fine, I'll get an IDE-to-CompactFlash adaptor, and install Xubunu on that. But wait, the computer DOESN'T HAVE AN IDE hdd interface, rather some ATA-5 interface, which I cannot find an adaptor for, at any price, anywhere. I have never seen such a connection on a hard drive. It has 44 pins, but I don't know if they line up to normal IDE pins, so even if I felt like soldering 44 30 guage wires to the connector, I don't know if it would work.

Cool, I can just install onto a USB drive! But wait, the computer won't boot from a USB drive.

Fine, I'll install onto the HDD, use GRUB to boot from the USB drive. But wait, apparently GRUB can't see the USB drives even, contrary to every normal computer I've ever seen.

So fine, I'll install Damn Small Linux, using the Frugal install which creates a ramdisk from the liveCD image stored on the hdd. Then I can use hdparm -Y *device* to turn off the hard drive. This works. I can even remove and replace the hard drive after booting with no problem. Except that I can't actually save anything when using this kind of install, so I can't make any kind of auto-flashdrive-mounting-and-slideshow-showing scripts, making the picture frame basically useless.

So apparently I might as well throw this thing in the trash, even after having spent $25 bucks on a nice shadowbox frame and matte.

---

