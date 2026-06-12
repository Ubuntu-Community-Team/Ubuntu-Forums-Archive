---
title: "Unable install Ubuntu 13.04 on P8H61-M"
date: 2013-06-03
forum: Hardware
---

### Post by pooherman on 2013-06-03
I can't to install Ubuntu 13.04 on P8H61-M2/TPM/SI motherboard , only if I add a acpi=off kernel option, then  booting and installing is ok. But after that I can't suspend and poweroff pc. I remove 'quiet splash $vt_handoff' from grub boot kernel options, loading is freezes on this lines:

BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
EDD information not available.

Can anybody help?

---

### Post by Bashing-om on 2013-06-03
[COLOR=#000000]pooherman; Hi ! Welcome to the forum.

I do not claim to be sharp tack in a box of tacks, in reference to all the knowledge within this forum, but, to me you are looking at a situation where your bios does not find a bootloader (grub).
If I might suggest:
Boot up the install media, note what boot parameters are "needed" in order to boot ubuntu (to the try ubuntu mode);
From that live media (re-)install grub onto the MBR of the drive(s);
Boot to the install's grub menu and add the "boot parameters" "needed" at the kernel boot line -> continue the boot process ;
--installing the recommended graphics driver at this point may resolve many problems--
Make the "needed" edits in /etc/default/grub file ;
update the configuration files for the changes to take effect:
```
sudo update-grub
```
Now re-boot to see the {a,e}ffects....[INDENT=2]
That is just my opinion[/INDENT]
 [/COLOR]

---

### Post by pooherman on 2013-06-04
Thank you, I'll try

---

### Post by Bashing-om on 2013-06-05
[COLOR=#000000]pooherman; Hi !

I trust all is going well. Please see my edit in that last post... the grub files need to be updated after any changes.
[/COLOR][INDENT][COLOR=#000000]
keep on keep'n on

[/COLOR][/INDENT]

---

