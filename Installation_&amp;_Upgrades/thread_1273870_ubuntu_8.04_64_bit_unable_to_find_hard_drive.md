---
title: "ubuntu 8.04 64 bit unable to find hard drive"
date: 2009-09-23
forum: Installation &amp; Upgrades
---

### Post by ctraxler on 2009-09-23
I am in the process of building a new machine.

Motherboard: EVGA X58 3X SLI
Processor: Intel Core i7-920 2.66Ghz 8M LGA1366 CPU
Video: XFX GeForce 9800 GT 512MB PCIe
Memory: Corsair Dominator 6144MB PC12800 DDR3

I did the bios update and went to install 8.04.3 desktop 64 bit.  I have a IDE DVD Drive and 750Gig WD SATA hard drive.  Upon running the install I get to the prepare partitions step and there are no drives listed.  

I have researched other threads and made sure the BIOS is set for IDE and am using Legacy Mode.  I also have the drive on Channel 0, although I am not sure that matters.  In any event, the drive will still not show up.  I also ran

SUDO fdisk -l

and nothing shows up on that either.  

I desperation I installed vista business 64 bit and that worked just fine.  

Any suggestions on how to resolve this?  I would prefer to have ubuntu as my primary os.  Any help is appreciated.

---

### Post by rreese6 on 2009-09-23
Seems like it might be BIOS issue.
sometimes the "Use PNP OS" set to yes causes trouble. change this and then auto detect the drives. save and reboot. see if this helps.
Might be that BIOS is not passing info to the installer.
I have heard of some motherboards not allowing SATA to communicate correctly with Linux such as epoch brand boards.
if Bios can see it, Ubuntu should also be able to see it.

---

### Post by gadolinio on 2009-09-24
Have you tried creating/managing your partitions with gparted? (boot from a liveCD, then go to system--administration--gparted partition editor).
Maybe if you create a new ext3 partition it will be shown then. You could also download and use (while in the liveCD session) disk-manager (i think it can be found in synaptic).
Hope you find this useful...

---

### Post by ctraxler on 2009-09-24
> **rreese6 said:**
> Seems like it might be BIOS issue.
sometimes the "Use PNP OS" set to yes causes trouble. change this and then auto detect the drives. save and reboot. see if this helps.
Might be that BIOS is not passing info to the installer.
I have heard of some motherboards not allowing SATA to communicate correctly with Linux such as epoch brand boards.
if Bios can see it, Ubuntu should also be able to see it.
 
Thanks.  This is a great new angle to attack.  I will not be able to try it for about a day, but will update the post with the result.

---

### Post by ctraxler on 2009-09-24
> **gadolinio said:**
> Have you tried creating/managing your partitions with gparted? (boot from a liveCD, then go to system--administration--gparted partition editor).
Maybe if you create a new ext3 partition it will be shown then. You could also download and use (while in the liveCD session) disk-manager (i think it can be found in synaptic).
Hope you find this useful...
 
I will not have access to the machine until tomorrow.  I will pursue this then and post the result.

---

### Post by ctraxler on 2009-09-24
> **rreese6 said:**
> Seems like it might be BIOS issue.
sometimes the "Use PNP OS" set to yes causes trouble. change this and then auto detect the drives. save and reboot. see if this helps.
Might be that BIOS is not passing info to the installer.
I have heard of some motherboards not allowing SATA to communicate correctly with Linux such as epoch brand boards.
if Bios can see it, Ubuntu should also be able to see it.
 
 
there is no choice on the bios for anything resembling "Use PNP OS" in any of the menus.  I was unable to try this.

---

### Post by ctraxler on 2009-09-24
> **gadolinio said:**
> Have you tried creating/managing your partitions with gparted? (boot from a liveCD, then go to system--administration--gparted partition editor).
Maybe if you create a new ext3 partition it will be shown then. You could also download and use (while in the liveCD session) disk-manager (i think it can be found in synaptic).
Hope you find this useful...
 
gparted does not find any drives either.  I have since put in two other SATA drives for a total of three.  Vista biz 64 bit finds them, ubuntu does not.

---

### Post by ctraxler on 2009-09-25
Anyone know if this would just be an installer issue?  I could always install on an IDE drive and then add the rest of the drives.

---

### Post by rreese6 on 2009-09-25
Adding the IDE drive seems like the easiest fix for now.
it would seem the the sata interface is not recognized by Linux yet.

---

### Post by ctraxler on 2009-09-29
> **rreese6 said:**
> Adding the IDE drive seems like the easiest fix for now.
it would seem the the sata interface is not recognized by Linux yet.

I had to move to fedora 11 for the host os as it recognized SATA drives out of the box.  I installed Ubuntu on an IDE drive and updated the sofware.   It still did not recognize any SATA drives in the box.  I have 5 SATA drives so moving everything to IDE did not make sense to me.  Hopefully this will get resolved for others.

Thanks for the help rreese6 and gadolino.  I appreciate it.

---

