---
title: "Dual-boot issue"
date: 2011-02-11
forum: Hardware
---

### Post by ge0rge04 on 2011-02-11
Hi.

I recently installed Windows XP SP3 and Ubuntu 10.10 in dual-boot, with grub as boot loader.

In order to make my Ubuntu work correctly (else it takes 1 minute to boot and i cannot shut it down without the halt command) , I must go in bios settings and set SATA operating mode to ENHANCED (I had to switch it on COMPATIBLE during the XP install). 

Now I receive a BSOD when I try to run XP, and one way to make it run correctly is to set back sata mode to compatible in bios.

How can I solve this issue? I don't want to switch that setting in bios every time I want to boot a different OS.

My laptop: Asus K70IO-TY014L
My HDD: Hitachi HTS54323

I guess it's a driver problem, but I'm not so experienced in this domain; on Ubuntu I just ran the update-manager.

---

### Post by oldfred on 2011-02-11
I saved this from another post. It is an XP issue. But I do not have have the instructions. Most instructions are for doing it while installing. It is more complicated to install the XP drivers after you have installed windows as I remember.

SATA mode should stay in AHCI unless you are getting nasty issues (which shouldn't happen with linux or vista/win7). The main reason why people change SATA mode to 'compatibility' is because winXP wont work with AHCI without loading the drivers..and you need a floppy drive to load the drivers, which most newer computers don't have (and lots of people are lazy anyway).

---

### Post by ge0rge04 on 2011-02-11
Ubuntu does nasty s#** on compatible mode (slow boot, freeze at reboot/shutdown), so leaving it this way is not an option for me.

The funny thing is that now i can't get even to the grub menu without the compatible mode. Back when Ubuntu used to be my main system, i had no problem running the sata enhanced mode.

---

