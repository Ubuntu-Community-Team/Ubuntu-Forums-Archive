---
title: "Bios repair using older motherboard"
date: 2009-01-16
forum: Hardware
---

### Post by Fisher on 2009-01-16
Hello. I was thinking if is there a way to make a bios update using a minimal Linux installation.
What I whant is the following:
- Boot the old machine;
- Get the bios image from other machine on tne network;
- Hotflash the bios on this old machine to "ressurect" others.

I have thinked to use something like slax or dsl to get a minimal os with network support, then copy the image over the net, and then boot to dos and use uniflash. But I would like to do this with only one bootup. Any ideas?
Oh, the old motherboard is a M585 from pc-chips, pretty cheap!!

---

### Post by electrogeist on 2009-01-18
I am not sure what the scope of your problem is.

Use PXE to push a DOS boot disk image with the flash utility and BIOS image?  [http://en.wikipedia.org/wiki/Preboot_Execution_Environment](http://en.wikipedia.org/wiki/Preboot_Execution_Environment)  That would prob work well if you had a lab of *identical* motherboards to update, and nothing is stopping them from booting.

Your use of the words "bios repair" and "resurrect" tho... do you have problems with the current BIOS that are keeping them from booting? On multiple machines?!?  Hot flashing is booting a pc with a good BIOS chip, then hot swapping in a bad one to reflash.  I don't know of any way to make one computer POST from the BIOS/image in another computer over the network.

---

### Post by Fisher on 2009-04-14
Cool!!
[IMG]http://www.threadbombing.com/data/media/2/Chuck_Norris_Approves.gif[/IMG]

---

