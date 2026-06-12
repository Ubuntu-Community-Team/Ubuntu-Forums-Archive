---
title: "Major Problem"
date: 2009-10-07
forum: Installation &amp; Upgrades
---

### Post by Bradart on 2009-10-07
Hi, i searched the forum but couldn't get any suitable results. I installed Ubuntu netbook remix on my acer aspire 1 to dual boot with xp.. The install went alright, but i had to install it twice due to a partitioning error (i made the partition too small the first time) and planned on going back in and manually formatting and resizing the smaller partition. So, when i get to grub, i select Ubuntu. Flawless execution, and i get in Ubuntu and happily play around. THEN I go to boot XP, and it hangs at the startup screen. No matter how long i wait, i just get that stupid windows logo staring at me. I checked, and all the files are intact. I HAVE to have access to xp, but for some reason, it just hangs there, PLEASE PLEASE PLEASE PEASE help. Thanks.

---

### Post by mikewhatever on 2009-10-07
Can you post the output of the following commands from Applications0<Accessories0<Terminal:

sudo fdisk -l
cat /boot/grub/menu.lst

---

### Post by ohiomoto on 2009-10-08
I had a similar problem with a UNR/Vista dual boot.  I doubt this applies in your case (due to differences in XP and Vista), but it might be worth a shot.

Here is what happened to me.  My Acer AS1410 came with Vista installed.  The BIOS setting for the SATA driver was set to AHCI, and UNR was hanging up on the splash screen after install.  When I changed the SATA BIOS setting to IDE mode, UNR worked but Vista would hang.  Since everything was fresh and I couldn't figure out how to get AHCI support in Ubuntu, I just reinstalled Vista with the BIOS set to IDE.  Everything works fine now.

The reason I don't think it applies in your case is I believe XP only supports IDE SATA drivers (I could be wrong.)  But you may want to change the setting in your BIOS and see what happens.  It's easy and you can easily switch back.

Good luck.

Edit: I should add that others have installed Ubuntu with the BIOS set to AHCI and had no issues at all.  Also, I don't see how installing Ubuntu would affect the BIOS/XP unless you changed your BIOS prior to install.  Like I said, I don't think my experience applies.

---

