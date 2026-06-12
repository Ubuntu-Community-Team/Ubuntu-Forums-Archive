---
title: "USB Key no longer boots after 9.10 update"
date: 2009-11-08
forum: Installation &amp; Upgrades
---

### Post by omro on 2009-11-08
Hi,

I installed 9.10 onto my USB key and set up the persistent filesystem. I booted up into the USB and ran the update manager. It flashed up a few things about GRUB and I left them at their defaults and moved on.

Now the USB won't boot.

Any ideas?
Thanks!

---

### Post by omegamormegil on 2009-11-08
I just had the same problem.  My USB live session with persistence would boot fine on one computer, but not on my laptop.  I fixed it by wiping the USB key and reinstalling the image onto it.  Hope that's helpful, but that's all I can suggest.

---

### Post by C.S.Cameron on 2009-11-08
My understanding is that it is not wise to run update on a "persistent" flash drive. It fills the drive with files that are difficult to remove and the kernel can not be modified anyway as it is just part of an image.
Better to do a full install to the flash drive, (using ubiquity). this allows full modification.

---

### Post by Mighty_Joe on 2009-11-09
> **C.S.Cameron said:**
> 
Better to do a full install to the flash drive

I agree.  I've had Live USB's stop booting after a couple of boots.  I've been running a 9.04 full-install on an 8GB flash drive for a few months.  Works great.

---

### Post by omro on 2009-11-09
Thanks for the info :-)

---

