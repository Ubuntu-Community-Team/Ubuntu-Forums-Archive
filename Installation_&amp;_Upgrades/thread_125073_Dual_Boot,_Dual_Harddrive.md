---
title: "Dual Boot, Dual Harddrive"
date: 2006-02-02
forum: Installation &amp; Upgrades
---

### Post by kgee on 2006-02-02
So after 12 hours of fighting with the installer, I come to the conclusion that GRUB and LILO will only install to the SATA drive on my system (as opposed to my maxtor) for reasons that I cannot begin to comprehend.

So I go with the flow and install Windows XP professional onto my maxtor, then Ubuntu onto my SATA. GRUB installs, it detects windows XP, and life goes on.

When the system reboots, however, Windows is not an option in the boot menu.

Technical details:

80 gig maxtor hd with windows on an NTFS file system,
80 gig SATA drive with Ubuntu on one large ext3

when the Ubuntu partitioner loaded (while installing Ubuntu) I noticed that windows was not listed. the harddrive it was on was present, but it did not say that there was either free space or windows. it was blank. looked something like this when i hit the continue button:

sda1 yada yada 80.3 GB ect.
hda1 yada yada 80.0 GB ect.
___ext3 something or other 78.5 GB  /
___ swap something something 1.5 GB  swap area


and i know that windows was on the sda1, even though it wasnt listed. The boot loader confirmed this when i installed it. but will not give me the option to load it.

Sorry if i am not making sence, It's nearly midnight where i am and I've been working on this one problem for 12 hours now. Any advice you could give would be greatly appreciated.

~Kgee

---

