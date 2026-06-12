---
title: "Dell Precision with SCSI hangs on boot"
date: 2005-10-25
forum: Hardware &amp; Laptops
---

### Post by hansjorn on 2005-10-25
Dell Precision WorkStation 610, dual Xeon with 2 built-in SCSI cards hangs when booting from Ubuntu install-disk.

The installers says something like:

DISABLING IRS #18

I have tried to start with options like: noapic, nolapic, aic7xxx=no_probe, aic7xxx=no_reset and finally: irqpoll

In the last case, the installer continued, but now it hangs when "Scanning CD-ROM" (which is on the IDE interface - only one unit is on the SCSI, and that's a tape unit).

The same server has recently run SuSE v9.2 without any problems - excpet the APIC has been turned off in the BIOS.

I really need the SCSI-interface, since we just bought a 200GB tape drive - so I need help to get it up and working.

Any help will most certainly be appreciated.

Hans Andersen
it-consultant
Royal School of Librarianship, Copenhagen, DK

---

### Post by bb002 on 2005-10-27
Just today I setup a server with a Adaptec 26190 (Think that's the number) and Ubuntu will hang for an entire minute after the kernel is loaded and the text "Starting Ubuntu..." is on screen. Have you tried waiting a minute or two. Or are you thinking it has crashed after 10-15 seconds and intervening like i was.

Also getting the model numbers and maker of the SCSI card will help greatly.

---

### Post by scoobs on 2005-10-30
I have an older Dell 410 dual processor machine and it too hangs for several mins when reaching the ubuntu message then eventually gets going again. I did have a bit of trouble configuring the scsi drives when I first took charge of this 2nd hand machine. Fiddling with the BIOS seemed to do the job. Not much fun for a confirmed Mac user though.

---

