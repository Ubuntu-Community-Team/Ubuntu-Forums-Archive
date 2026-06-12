---
title: "Cannot finish boot or recovery mode"
date: 2009-06-12
forum: Hardware
---

### Post by wisd0m on 2009-06-12
When I got home today my wife said that my desktop was not able to connect to the internet. I reset the machine and waited.

It loaded grub and went to the splash screen, then froze. It would not boot past the splash screen. I rebooted several more time and got the same result.

When I tried recovery mode, it would not load either.

I then tried to boot from USB, only to have it freeze on the splash screen as well.

I have no idea what is wrong. Please help.

more info:

As my sig says, I have an intel e4600 2.4Ghz, 4GB DDR2 RAM, Gigabyte EP35-DS3L board, ATI POS, 120GB/250GB/500GB HDDs in an Antec 380w case.

I DID have a fairly large thunder storm in my town this morning, and the power could have gone off or surged. If the storm caused this, what part of the computer would be broken and how would I know?


Thanks for any help. :(

---

### Post by baizon on 2009-06-12
Have you made an memtest?

---

### Post by Kevbert on 2009-06-12
As Baizon suggests run memtest86+ from the boot menu for a couple of passes. If that works, try running a Ubuntu Live CD, as it could be a corrupted file system.

---

### Post by irv on 2009-06-12
Choose Recovery from the grub and see where it stops at boot up. It might give you some information on what is going on.

---

### Post by wisd0m on 2009-06-12
> **Kevbert said:**
> As Baizon suggests run memtest86+ from the boot menu for a couple of passes. If that works, try running a Ubuntu Live CD, as it could be a corrupted file system.

Live CD (Live USB) stops booting at the same point the HDD does.

I did not run memtest yet, but will try it.

---

### Post by jbruced on 2009-06-12
> **wisd0m said:**
> Live CD (Live USB) stops booting at the same point the HDD does.

I did not run memtest yet, but will try it.

Unfortunately sounds very much like a hardware/bios failure.

Have you tried resetting your bios cmos?

Maybe even removing the battery and reinstalling to reset cmos/bios may help, electrical spikes can screw with cmos settings.

GL
Bruce

---

### Post by wisd0m on 2009-06-12
I unplugged everything (gave it a little vacuum) and put it back together. 

Ran memtest, then booted into recovery mode. It worked. I then booted normally.

The computer seems to be working now. I think unplugging everything helped.

I now have NO network connection. I have tested the cat5e cable with my laptop and confirmed the the cable is connected to the router and the internet.

When I run ifconfig eth0 i get the mac address and sudo ifdown eth0 says: "interface eth0 not configured"

This is an onboard NIC, how do I "configure" it?

thanks for the help everyone.

---

### Post by solarmd on 2011-02-20
I now have my two laptop PC's with dual boot Windows7 and Ubuntu 10.04 and 11.04 alpha, one in the same condition --hangs with splash screen, one boots into a new 
user-interface, FileManager, and Applications... but with crippled capabilities.
 
The 11.04 machine( Acer with TK42, Vision video) was nursed to current condition via a couple of runs in from Recovery mode.
 
Question I have now is How & where can I learn about Recovery mode?
In my other NBPC, an HP Quadcore i5 cpu with 4GB, I was not able to get Recovery
mode capability. It does boot into the Grub mode prompt. I am at a loss on what I
can do.
Also, I like to learn more about the Grub. 
 
Thanks for any help.

---

### Post by snoopy-2009 on 2011-03-09
jeez.. i had the same issue.. i tried a memtest, and correct me i im wrong, but does it just go vorever? lol wall time was at like 2 and a hal hours beore i escaped out. im not sure iv this vixed anything at all or not.. but i attempted booting usb again, seemed to hang in the same place, but i came back home an hour or so later and it was booted.. now its currently hung on the screen where theres the three chekmarks (2.6g avail, power source, and internet connection) once i hit next, it hangs, i suppose im just gonna leave it vor a while again, and see iv i ever makes it through it.. (i was dealing with this same issue earlier this am, b4 i had any splash screen hangs.. and it never seemed to recover, which is why i tried re-creating the usb numerous times, and such.) ive also tried installing via the live cd, but it seems to haave a wide variety ov error popups, so i did not want to even attempt installing that way. did not seem to be a smart idea.. lol

---

