---
title: "Vantec 11 in 1 Card Reader"
date: 2010-06-25
forum: Hardware
---

### Post by belkinsa on 2010-06-25
Based on their product page ([http://www.vantecusa.com/en/product/view_detail/257](http://www.vantecusa.com/en/product/view_detail/257)), I know they don't have a Linux driver.  Just a wonder, is it possible to get the drive it?

Thanks.

---

### Post by efflandt on 2010-06-26
I don't know about that unit specifically.  But I have not had any trouble with any USB flash memory or USB card readers in Linux.  It should all appear to be usb mass storage, like just another hard drive.  I have even booted the live Ubuntu iso from microSD in a SD adapter in a USB card reader.

I did have trouble with one old laptop not auto mounting USB or CD/DVD's, but that was because Linux kept polling for a non-existing floppy in a hot swap drive bay.  And once I blacklisted floppy module (and did sudo update-intiramfs -u) it ignored the phantom floppy and auto mounting worked.

---

### Post by belkinsa on 2010-06-26
I don't have any trouble with my other removable media, just this one.  Maybe what my dad told me about the USB cord holds true even with Linux.

---

