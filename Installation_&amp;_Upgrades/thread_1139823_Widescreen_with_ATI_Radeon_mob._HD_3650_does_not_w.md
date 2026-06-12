---
title: "Widescreen with ATI Radeon mob. HD 3650 does not work"
date: 2009-04-27
forum: Installation &amp; Upgrades
---

### Post by themw on 2009-04-27
Hello
 
I installed 9.04 on my Laptop (Toshiba A 350, Intel C2D T6400, 4 GB RAM, 320 GB HDD, ATI mobility Radeon HD 3650, 1366x768 pixel resolution).
 
I tried several versions of different drivers with listed results:
- ATI: version 9.2 .. 9.4: at startup X freezes with blank black screen - system has no reaction (tested on 8.04 32 bit, 9.04 32bit, 64 bit)
- RadeonHD: X comes up, exits and says that vendor string is not available (also tested with 8.04, 9.04 32bit, 64 bit)
 
manual changes to xorg.conf resulting in startup with vesa in 800x600.
 
I tested all i can imagine: manual installation (compiling + make install for RadeonHD, installing newest driver from ATI / AMD homepage (version 9.4))
Also installation of pakets from repository don't work.
 
Now I use the VESA . mode with 1024x768 - which looks quite awful.
 
Can anybody help me please?
 
thanks a lot
 
themw

---

### Post by TheBeet on 2009-04-27
I have the same video card in my Toshiba A355, and I've done just about the same stuff you have to no avail. I think the bug was reported on launchpad, and I haven't seen any updates recently.

---

### Post by themw on 2009-04-28
Hello 
 
Is there a temporary solution to show the widescreen resolution instead of the 4:3 (maybe with other drivers (Radeon(HD) or VESA))?. Because of the stretching, I can't use my ubuntu and i'm forced to use Windows. :cry:
 
Any help is very appreciated!
 
themw

---

### Post by mcmatom on 2009-04-30
> **TheBeet said:**
> I have the same video card in my Toshiba A355, and I've done just about the same stuff you have to no avail. I think the bug was reported on launchpad, and I haven't seen any updates recently.

Let me preface this by saying I am a total noob to all of this.  I have the same model Toshiba and was attempting to create a dual boot of Vistax64/Ubuntux64 (following the instructions found here: [http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm](http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm)).  I only got as far as choosing to install Ubuntu from the boot CD.  At that point the DVD drive spun for a few seconds and my screen went black.  I imagine my symptoms are all related to the problem in this thread.  I guess that also means my vision of a dual boot is DOA at this point.

I was wondering if you could provide a link to the issue you mention in Launchpad so I could follow its progress?

Thanks in advance.

---

### Post by TheBeet on 2009-04-30
> Let me preface this by saying I am a total noob to all of this. I have the same model Toshiba and was attempting to create a dual boot of Vistax64/Ubuntux64 (following the instructions found here: [http://apcmag.com/how_to_dualboot_vi...lled_first.htm](http://apcmag.com/how_to_dualboot_vi...lled_first.htm)). I only got as far as choosing to install Ubuntu from the boot CD. At that point the DVD drive spun for a few seconds and my screen went black. I imagine my symptoms are all related to the problem in this thread. I guess that also means my vision of a dual boot is DOA at this point.

I was wondering if you could provide a link to the issue you mention in Launchpad so I could follow its progress?

Thanks in advance.
2 Days Ago 12:02 AM

Just making sure you know this, but for the mean time, you can install Ubuntu using Safe Graphics Mode, which will allow you to use the GUI until this gets resolved. (If I've offended your noobness, I apologize :) )

---

### Post by themw on 2009-05-05
Hi TheBeet,
 
I see, that you also have the hardware-configuration with 4 GB of Ram. Have you solved the problem on your machine? 
Starting in safe grafics mode is not the best option since the all things displayed are stretched.
 
Do you know, if the work on this problem is going on?
 
Thanks and best regards
 
themw

---

### Post by mcmatom on 2009-05-06
Thanks TheBeet.  I ended up going a different direction.  I installed VirtualBox and then installed the x86 version of 9.04 and it works like a charm.  For my needs this was probably a better solution than the dual boot.  It would be nice if VirtualBox support x64, but that will come soon enough.

---

### Post by Dawnthorn on 2010-01-25
Someone finally figured out a real work around. If you add "pci=use_crs" to your kernel boot options the screen will work with 4GB of memory at full resolution.

---

