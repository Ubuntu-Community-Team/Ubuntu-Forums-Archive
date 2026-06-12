---
title: "Does Lucid run on a MSI A6205"
date: 2010-07-31
forum: Hardware
---

### Post by drlinux on 2010-07-31
I have just bought a MSI A6205 laptop and found that the Lucid live CD and it runs fine.  However I have recently read on another thread that somebody with the same model did a clean install of lucid and and when they activate the suggested ATI driver for the ATI Radeon HD5470 card they get a blank screen - see below:

 [I][B][ubuntu]  ATI mobility Radeon HD 5470
Views: 12,684
Posted By timpaton
Re: ATI mobility Radeon HD 5470

No such luck here.
[/B][/I]

[B][I]I'm installing on a MSI A6205 (i5, ATI HD5470). Rebooting with the fglrx driver enabled gives me a blank screen.

The system is still working in the background - it shuts down...[/I][/B]

Is anybody out there successfuly running lucid on this laptop?:)

---

### Post by dino99 on 2010-07-31
the good news: if it work on live cd, it might work too when installed, only need some tweaks

boot by adding nomodeset on the boot line (hold "shift" key down at end of bios process if grub menu is hidden, then edit (E) the boot line: add nomodeset and remove quiet splash to let you know and see what happen when booting, then boot (ctrl+X))

---

