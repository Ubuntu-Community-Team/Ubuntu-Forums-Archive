---
title: "Dell Latitude E5570 SSD &amp; Video problems"
date: 2016-07-05
forum: Hardware
---

### Post by dpcole72 on 2016-07-05
GREAT question!

I got my new e5570 today - awesome machine - but when booting 16.04 (Ubuntu Studio edition), even using **i915.preliminary_hw_support=1 **as a special parameter, no HDD was found (I've the 512GB SSD model, and the unit didn't come with the bracket allowing a standard HDD to be installed alongside...)

Will be ordering the bracket and hoping the regular HDD interface will work.  

Still researching how to make the integrated m.2 SSD be recognized.  Wifi seems to work out of the box, which is a big plus.  But not seeing the drive is a small minus.

---

### Post by X-RED_Tech on 2016-07-05
You may need to change RAID to AHCI at the UEFI settings for drives.

---

### Post by dpcole72 on 2016-07-06
D'oh!  Thanks for the tip, I completely forgot about that.  

Dell indeed does it set to RAID by default.  

As a result of changing it to AHCI (which it ought to be in general for laptops, IMHO), I got the expected-but-forgot-about BSOD for "inaccessible device" (due to different driver not existing).  I'm resetting the PC (which is new, anyway) and once Win10 is back I'll set up the laptop as dual-boot (all on a 512GB Samsung "Class 40" SSD, whatever that means since there is no unified standard as such).  I downloaded the recovery disc and will be making a bootable Win10 DVD too...

It's a shame compression isn't advisable for SSDs...

Will report back later today with an update.  I've got Crossover Office and VMWare for VM Windows sessions if needed (certainly for Visual Studio, if I need to do .NET programming... otherwise I'm happy with Eclipse...)

I will say this, the display (while not touch screen) is largely awesome.  MVA panel, I reckon, due to grayscale sheen but no hue shift...

---

### Post by dpcole72 on 2016-07-08
Okay, found a problem - according to my purchase receipt my laptop has an AMD R2 360 video card.  Ubuntu Studio 16.04 did not install it, using the Intel 530 GPU instead.  Is there a manual way to install the AMD driver?

Thanks!

---

### Post by DuckHook on 2016-07-08
*Post moved to its own thread in **Hardware** with a new and more appropriate title.* Also, just a friendly reminder not to hijack other's threads.

---

