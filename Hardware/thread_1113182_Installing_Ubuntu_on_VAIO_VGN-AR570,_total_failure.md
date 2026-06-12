---
title: "Installing Ubuntu on VAIO VGN-AR570, total failure"
date: 2009-04-01
forum: Hardware
---

### Post by andre.fabbro on 2009-04-01
Hello everyone,

I tried hard to install the **Ubuntu 8.10 **on my laptop **VAIO VGN-AR570**, but it was unsuccessfully, a total failure. :cry:
The problem I think can be related with the fact that my laptop has two 120GB HDD SCSI in RAID0, and I don't know if the graphical default installation is appropriate to install with these features.
The installation didn't recognize the RAID0 configuration, that detected two 120GB HDD instead one of 240GB.
I tried the three partition options of the HD, everything looks fine but at the end of installation, but when the system is restarted, the following terrible error occurs:

> GRUB loading stage 1.5.
GRUB loading, please wait...
Error 2

I’ll really appreciate any help, I'm newbie in Ubuntu but I want to throw the MS Vista finally into the trash. ;)

---

### Post by argosreality on 2009-04-01
Did the system come configured in a raid configuration from Sony? If so, the ubuntu installer should only see the combined 240Gb. The Sony uses the standard Intel integrated RAID so to enable RAID0 you'd have to go either into the BIOS or else after the initial BIOS screen disappears you should also see one about Intel raid management.

---

### Post by andre.fabbro on 2009-04-01
Yes, came configured from Sony. In fact I didn't know that my laptop it's RAID0, I discovered when tried to install Ubuntu, my BIOS shows two HDD, and the Ubuntu installation also detected two, but the windows setup only one... is that the really reason for failure on grub? What should I do?

---

