---
title: "Booting to external hard drive"
date: 2007-05-22
forum: Hardware &amp; Laptops
---

### Post by captainmnb on 2007-05-22
I'd like to install Feisty on my Lenovo X41 tablet, but I need to preserve Windows because of a few specific programs.  The internal hard drive is only 60GB, not enough for a dual boot, so I am trying to transfer my Windows install over to a USB external hard drive (SimpleTech 120GB), and then boot from that.  I tried using both fdisk and gparted off of a Feisty LiveCD to partition the hard drive (I only want 50GB or so to be used for the Windows install, the rest for storage), and then Acronis TrueImage from Windows to make the image transfer, but when I tried booting, the BIOS failed to even recognize the hard drive.  I am almost positive that the BIOS supports booting from USB hard drives, but when I go into the boot list, it is not listed.  I set the boot flag, but no luck.  I've even booted from a USB flash drive on this computer before.  Any ideas?

---

### Post by matburton on 2007-05-23
Hey,

I have a 60GB hard disk and I dual boot :p (I know that's not helpful)

I have to admit though that I was under the impression that Windows can't boot from USB drives (all except early Betas of Vista that is) so that might already be a sticking point?

When you transferred the image of the partition did it also copy the MBR?
If not then you need to write one to the USB hard disk to be able to boot from it I would have thought.

Hope that's some help ;)

---

