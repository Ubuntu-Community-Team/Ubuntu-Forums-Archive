---
title: "boot puppy linux from flash drive"
date: 2007-06-03
forum: Hardware &amp; Laptops
---

### Post by newbemac on 2007-06-03
I have a toshiba satellite A85-S107 laptop and want to boot puppy linux from a flash drive.  the bios will not allow be to do so, only from the cd drive, any thoughts on home to get the bios to see the USB flash drive first??
mac

---

### Post by bone43 on 2007-06-03
> **newbemac said:**
> I have a toshiba satellite A85-S107 laptop and want to boot puppy linux from a flash drive.  the bios will not allow be to do so, only from the cd drive, any thoughts on home to get the bios to see the USB flash drive first??
mac

Only if in your bios it allows you to boot from a USB device, if so set it to be the first boot device and it should work.

---

### Post by newbemac on 2007-06-03
Well...
My bios screen displays my cd drive, my HDD, and something labeled as FDD,  I did not select this as I don't know what it is or what will happen if i do??
mac

---

### Post by taylorsnow on 2007-07-07
FDD = floppy disk drive

looking like its not an optioin, may want to research this, but a buddy of mine had a CD that he had that would somehow force boot to a USB drive. I dono what it was but its a start for ya.... seen it first hand... 

good luck.... also why not just run it from a CD?

---

### Post by smoker on 2007-07-07
as taylorsnow stated, FDD is your floppy drive, with puppy you can create a boot floppy that will direct your bios to look to the usb for the bootable operating system.

also, you could try enabling anything referring to usb in your bios setup, on my bios, i can boot from usb, but the flash drive is recognized as a second floppy device! sometimes your usb may be regarded as a zip drive, it is a matter of trial and error.

---

