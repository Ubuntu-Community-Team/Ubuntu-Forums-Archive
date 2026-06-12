---
title: "Setting up Ubuntu on Dual Boot Raid"
date: 2009-11-06
forum: Installation &amp; Upgrades
---

### Post by oli847 on 2009-11-06
Hi, I'm (almost) completely new to Ubuntu, so I was wondering if anyone could help me with this. I've recently installed Win7 on a RAID1 Array, and it took me ages to back it up sort it all out and get back to using it properly after running the release candidate for 6 months (built the PC then), so I don't want to lose that. What I want to do is install Ubuntu onto another HDD and dual boot that with Win7. 
 
a) Is this possible?
 
b) How do I do it?
 
The Raid array is SATA 2*25GB Excelsior HDDs
Mobo is Asus P6T se
Processor is core i7 920
6GB 1333 Corsair Ram
Nvidia GTX 295
 
The other HDD I have handy is an IDE, but I could proably dig up a SATA from somewhere if needs be.
 
Thanks in advance for any help you guys can give.
 
 
Oli

---

### Post by Cr0n_J0b on 2009-11-06
I'll give you a bump for this...though I'm not sure exactly how to do it.

If it were me, I'd remove the RAID1 set, do the install of ubuntu on the 3rd drive and check to make sure it's what you want.  Once you do that it will be up to the BIOS to pick which one it wants to boot first...you can help it make that decision with an f2 at boot...or f8 or whatever your BIOS asks for.  Set the boot order as you see fit.

Once you booted your preferred OS, you need to add the other device to the boot loader of that system.

The reason i'm saying it this way is that you can use the Win7 boot loader or the Grub loaded (I think).

This is where my advice ends.  I don't dual boot.

---

### Post by oli847 on 2009-11-07
Quick update, I now have Ubuntu installed on the non-RAID disk, but to boot to either that or Windows 7, I have to change the order of the disks in the bios.  If I set the RAID array as first disk, tehn I get the windows OS chooser thingy, but if I choose Ubuntu it hangs and says media not found or something similar.  If I set the non-RAID disk as first, I get the GRUB screen with all the Linux options, and Windows 7, but If I choose Windows 7, again, media not found type of error.  By Mobo is an ASUS P6T SE...

---

