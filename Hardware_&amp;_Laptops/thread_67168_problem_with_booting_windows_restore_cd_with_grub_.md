---
title: "problem with booting windows restore cd with grub (toshiba satellite laptop)"
date: 2005-09-19
forum: Hardware &amp; Laptops
---

### Post by digital on 2005-09-19
unfortunately, for some practical application purposes, i need to switch my toshiba satellite laptop back to the default windows os.

as of right now i am running hoary 5.04 with the grub bootloader.
the problem is that i cannot get the bios to run my windows restore disk.

with the toshiba bios on my laptop, you can arrow over when the toshiba logo is up to choose the boot order, IE hard drive, cd, etc, but when i choose to do this currently, the cd will not boot up and it will default to the grub bootloader.

i don't know what the problem could be, if grub is overtaking my bios settings or it just is a conflict.

does anyone have any ideas how i can restore either my bios, or stop grub from loading. or even, to completely format my disk.

any help would be appreciated.

thanks.

---

### Post by mlomker on 2005-09-19
> does anyone have any ideas how i can restore either my bios, or stop grub from loading. or even, to completely format my disk.


It isn't possible for grub to over-ride your BIOS because the BIOS loads grub.  Are you sure that the disc isn't defective?  Have you tried booting with it on another machine?  Have you tried using another bootable disc on your laptop?

You could boot to almost any linux liveCD and format your drive, but that's not going to help if you can't boot your XP CD.

---

### Post by Hobbsee on 2005-09-20
toshiba satellite?  Yep, got one of them.

Not sure what you mean about the mouse-over the toshiba logo - i just hit escape from when i boot the machine, then hit F1 when it tells me to.  After that, it loads the pretty blue bios screen, where I change my boot order.

As for getting rid of grub, it can be done, so long as you then tell your machine to boot to CD first, and use the toshiba recovery CD, which will restore your machine back to the original - you did keep those 3 packaged cd's for a reason, didnt you!  :P

Still looking for the exact command to get rid of grub, as the fixmbr on windows doesnt work with the toshiba recovery cds...i know it exists, as i've used it before...

---

### Post by digital on 2005-09-20
when i hit escape and then it tells me to hit F1, i don't get a bios screen, it just flashes right to grub.

any other ideas?

---

### Post by Hobbsee on 2005-09-20
[QUOTE=digital]when i hit escape and then it tells me to hit F1, i don't get a bios screen, it just flashes right to grub.

any other ideas?[/QUOTE]
 that's weird!

Google suggests this:
From [http://www.experts-exchange.com/Hardware/Laptops_Notebooks/Q_20867289.html](http://www.experts-exchange.com/Hardware/Laptops_Notebooks/Q_20867289.html)

> [http://www.csd.toshiba.com/cgi-bin/tais/su/su_sc_docFrm.jsp?BV_SessionID=@@@@2139020824.1075417564@@@@&BV_EngineID=cccjadckifkjmlicgfkceghdgngdgli.0&file=%2fcontent%2fsupport%2fmanuals%2fuserguides%2fSatellite%2f4080XCDT%2f%2fchap0007.html&moid=1073769736&soid=112299](http://www.csd.toshiba.com/cgi-bin/tais/su/su_sc_docFrm.jsp?BV_SessionID=@@@@2139020824.1075417564@@@@&BV_EngineID=cccjadckifkjmlicgfkceghdgngdgli.0&file=%2fcontent%2fsupport%2fmanuals%2fuserguides%2fSatellite%2f4080XCDT%2f%2fchap0007.html&moid=1073769736&soid=112299)

You can access the BIOS settings on these models using any one of these 3 methods.

From the Windows Control Panel, launch the Toshiba HWSetup program. HWSetup provides a user-friendly graphical frontend for modifying BIOS settings. Please note that if you change some settings, you may be required to restart your computer. HWSetup comes preinstalled on your Toshiba portable PC, or it can be downloaded as part of the Toshiba Utilities package for your model.

Press the [Esc] key while the system processes its Power On Self Test (POST). In order to use this method, the computer must be "off", meaning not in sleep/suspend or hibernate mode. Press the power button, then immediately press the [Esc] key (it doesn't hurt to hold the key down). When the POST finishes, you'll be prompted to press the F1 key to enter BIOS setup. Press the [F1] key to access the BIOS setup program.

From MS-DOS, run the TSETUP program. TSETUP must be run under real mode DOS (not a Windows-based MS-DOS prompt) with no memory manager (like HIMEM.SYS, QEMM386, or equivalent) installed. TSETUP was provided originally with your computer, or you can download it from this Website

I couldnt get the first link on that to work, but that may be a small help...

which model satellite is this?  toshiba has various bios upgrades, but I have no idea if they make any difference...

---

