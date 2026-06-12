---
title: "Help booting Ubuntu from an external hard drive"
date: 2007-05-18
forum: Hardware &amp; Laptops
---

### Post by Yes on 2007-05-18
Ok, I would like to use Ubuntu, but the rest of my family wants to keep Windows.  I would like to get an external hard drive, and boot Linux from there.  I need to know what hard drive you would suggest, and how to install Ubuntu on that hard drive.

I'll be able to set the external hard drive as the hard drive the computer boots from, right?  That way, I can just unplug the external hard drive to boot Windoes, and plug it back in to boot it from Ubuntu?

Thanks!

---

### Post by Dekunuts on 2007-05-19
It is certainly possible to do that, but an easier solution might be to just put a second hard drive in your computer and install linux on that one (make sure to select the right one while installing:), you can make it easily recognizable by making sure the new hard drive is a different size than the one already in there). 

You can also dual boot from the very same hard drive, but then your winxp installation would have to give up space for the ubuntu one, thus annoying your family.

If I was you, i'd go with my first suggestion.

---

### Post by mikewhatever on 2007-05-19
> **Yes said:**
> Ok, I would like to use Ubuntu, but the rest of my family wants to keep Windows.  I would like to get an external hard drive, and boot Linux from there.  I need to know what hard drive you would suggest, and how to install Ubuntu on that hard drive.

I'll be able to set the external hard drive as the hard drive the computer boots from, right?  That way, I can just unplug the external hard drive to boot Windoes, and plug it back in to boot it from Ubuntu?

Thanks!

Two important points to keep in mind:
1. GRUB boot loader must be installed to the MBR of the external HDD. This way, when the external HDD is connected, the PC will boot from it and load GRUB.
2. The boot order must be set in the BIOS to boot from the external HDD before booting from the internal one. This way, if the external HDD is not connected, Windows boot loader would load.

---

