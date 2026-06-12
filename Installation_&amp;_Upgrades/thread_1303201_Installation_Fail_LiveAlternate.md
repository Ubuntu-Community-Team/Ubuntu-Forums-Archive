---
title: "Installation Fail Live/Alternate"
date: 2009-10-28
forum: Installation &amp; Upgrades
---

### Post by Meech2K on 2009-10-28
I've searched and tried:

reburning
alternate install
usb install
various options:
  irqpoll
  pci-nomsi
  all_generic_ide
  all-generic-ide

to no avail.   Live CD dumps to busybox (whether it's try mode, install mode, or check disk mode)   Alternate fails with "Installation cd-rom couldn't be mounted"

I have a vanilla-ish setup with Quad core, Intel board, 1 SATA HDD, 1 PATA DVD, Nvidia 8800, 4GB (using x86 install).

Christ, by 9.04 can't we just stick the CD in and goooo?

I'd really like to get ubu running, but I'm on the edge of....  either saying f'it and trying a different distro or going virtual.

I know the drive, and everything else works -- just finished installing Win7 :p

---

### Post by Dark_Stang on 2009-10-28
Have you tried running the AMD64 disc? You do, afterall, have a quad core and 4 gigs of memory. I also remember some Intel boards were having issues with Linux, perhaps somebody with some experience on that cam chime in.

---

### Post by Meech2K on 2009-10-28
I haven't tried the x64 version.

I have a sneaky suspicion that it's related to the DVD on PATA -vs- the HD on SATA.

Just frustrating that a relatively plain setup requires so much work.  And it's still not working ;p

---

### Post by Meech2K on 2009-10-28
In case anybody else is battling this, I bought and installed a SATA DVD.

Just as I expected, LiveCD boots fine -- I'm posting this from the Jaunty LiveCD.

Next up -- installation.

---

### Post by Dark_Stang on 2009-10-28
Are you sure your old PATA/IDE optical drive wasn't failing? I haven't seen that issue before. Also, why not install 9.10?

---

### Post by Meech2K on 2009-10-29
> **Dark_Stang said:**
> Are you sure your old PATA/IDE optical drive wasn't failing? I haven't seen that issue before. Also, why not install 9.10?

Yes, I'm sure.  I've burned several DVDs and just, just finished installing Win7 on a new MB/HD.  Never had any issues with the drive.

In my quest to find a solution, it seems like there are a lot of issues with the SATA HD/PATA DVD combo,  particularly with the Jmicron controllers.

I'll upgrade to 9.10, after downloading 3 times, burning, etc.  I was just happy to get something running.  :D

---

