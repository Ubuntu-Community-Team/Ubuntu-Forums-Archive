---
title: "Booting install disk from a built-in SD card reader"
date: 2013-02-14
forum: Hardware
---

### Post by ofnuts on 2013-02-14
If the machine has a built-in SD card reader, is it possible to boot an installation from it (in general, and in particular for the Thinkpad T series)? The built-in card reader seems to be faster than a USB key in a USB port... Is there anything special to do for this (besides making sure the BIOS includes the card as a boot device)?

---

### Post by C.S.Cameron on 2013-02-14
My 8 year old Asus laptop will not boot from SD card but all of my newer computers will.

You should be able to use a Live or Persistent install made with Startup Disk Creator or Unetbootin, or you can do a Full install if the card is larger than 4GB.

I am not sure that it is faster than a regular USB stick though.

---

### Post by ahallubuntu on 2013-02-14
~

---

### Post by ofnuts on 2013-02-15
> **ahallubuntu said:**
> Yes, sometimes your SD card reader is bootable, sometimes not.  Depends on the design of the computer it is attached to.  I have a couple of laptops that will boot the SD card reader and some that won't.

Here's a secret, though: internally, the SD card reader may well be attaches as if it were connected to a USB port.  That is, if you buy an external card reader, plug in the same SD card, and connect that to a USB port, the speed should be about the same either way.  Performance of flash cards (USB, SD, etc.) varies depending on the flash chips used inside.  Some are faster than others; some are a LOT faster than others.  That could be the real reason why one seems faster than another.

Yes, I know the built-in reader is really using the USB internal bus. But the reader is faster (reading a plain 2GB file from the built-in readeris 15% faster than using a good external card reader. And the typical case (reading photos) is much faster in practice.

---

