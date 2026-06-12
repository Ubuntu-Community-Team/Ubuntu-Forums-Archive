---
title: "Trying windows 7..."
date: 2009-08-03
forum: Installation &amp; Upgrades
---

### Post by logicalform on 2009-08-03
I have decided to try out windows 7 for kicks and have downloaded the RC. I want to install it on my second distro partition (sd3) which currently houses sabayon 4.2 (my linux mint (ubuntu) is on sd1). 
-Do I need to use gparted to first format that partition or can I do that from the installer (will the installer recognize the ext4 linux partition)? -Also, what do I do about saving or restoring grub so that I can choose not to go straight to windows (I don't want it as my default). 
-Since I installed sabayon last does that mean that destroying that partition will mess with my grub? 
-Finally, is there a way to access my sd1 media files from windows or will I have to create a fat32 partition to share things between OSes?

Thanks for any help or guidance anyone can give me

---

### Post by darco on 2009-08-03
Why dont you install VirtualBox or VMware Server (both are free) and then create a vm of Win 7? Then you can really decide if you want Win7 on its own partition.


darco

---

### Post by ninjapirate89 on 2009-08-03
> **darco said:**
> Why dont you install VirtualBox or VMware Server (both are free) and then create a vm of Win 7? Then you can really decide if you want Win7 on its own partition.


darco


This is probably the best option (also the choice I made) since win7 is still in the RC stage. Once it is officially released then you can consider making a permanent installation.

Edit -> Oh and btw, win7 is very nice. Would be fun to use on one of those touchscreen desktops.

---

### Post by GregMcn on 2009-08-03
Yep i agree with others.Use Virtualbox or Vmware.That way you wont screw up your linux partition.I always use it to try out new versions of linux.

---

### Post by darco on 2009-08-03
I read somewhere that KVM (?) is working on a pci-pass through meaning you may be able to access the full power of your vid card! That would be awesome!. Then I would wipe my partition of Windows...

darco

---

### Post by logicalform on 2009-08-04
So I decided to take you guys' advice and try out virtualbox, but I'm having trouble installing w7 with it. It keeps telling me that windows failed to start, and giving me the directions:

1) insert windows installation disc and restart computer
2) choose language settings and then click next
3) click repair your computer

Also, under "info" it says "attempting to load a 64-bit application, however this cpu is not compatible with 64 bit mode". Can I not use the 64 bit version with virtualbox? Or am I just not doing things right? 

Any help is greatly appreciated.

---

