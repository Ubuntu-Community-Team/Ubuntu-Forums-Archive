---
title: "Trying to install UNR 9.04 to SDHC card on Acer Aspire One"
date: 2009-10-21
forum: Installation &amp; Upgrades
---

### Post by pauljchang on 2009-10-21
I'm having trouble installing UNR 9.04 to my Acer Aspire One SDHC card.  I know that, unlike other netbooks/laptops, the SD slot is not a USB device, but rather a PCIe device, which means that the BIOS cannot boot directly from the SD slot.  I've read some rather complicated ways to work around this, but after trying them, I'm still unsuccessful.

One option that I've heard suggested is to install to the SDHC card while it's in a USB SDHC reader, and then boot from it, record the UUID of the SD card, and then reconfigure GRUB.  Unfortunately for me, after installing to my SDHC card this way, I am not able to boot from it even when it's in a USB SDHC card reader.  I've tried two different SDHC readers and neither is recognized by the BIOS as a valid USB bootable device, though it has no problem booting from a USB stick.  So because I can't boot from the SDHC card while it's in a reader, I'm unable to proceed with this method.

Another method I thought I'd try is to create a small /boot partition on my SSD drive, but leave the / and swap partitions on the SD cards.  This method will allow me to boot into /boot, but because the SD drivers are not loaded, it only boots partially and then drops me to the shell, unable to find the / partition on the SD card.  Is there an easy way to modify /boot to load the SD drivers so that UNR can see the other partition?

I would love to simply do a full install on the SSD, but I need to use crappy, bloated Windows, where, even though only the OS and some small programs are installed, it still seems to fill up over 6GB of my precious 8GB of SSD space.

So, just seeking some advice on how best to proceed.  Thanks for reading my thread!

---

