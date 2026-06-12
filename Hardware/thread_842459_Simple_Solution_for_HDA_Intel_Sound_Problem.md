---
title: "Simple Solution for HDA Intel Sound Problem"
date: 2008-06-27
forum: Hardware
---

### Post by maulik001 on 2008-06-27
I just put Linux on my Toshiba P100 laptop and my sound was not working at all... so of course I searched the internet for a solution and found that HDA Intel has a problem and and a bunch of solutions that work or dont work, so heres one more...

This worked for my toshiba laptop and should work with most toshibas, not sure bout other manufactures but you can always give it a shot.


1. Reinstall Ubuntu if u changed anything in a attempt to fix the sound.
2. Download your latest BIOS.
3.Install WINE so you can open the BIOS installer.
4. When you open it you should get a choice to make a BOOT CD from the iso image in the BIOS package.
5. Reboot with the BOOT CD to install BIOS
6. When computer starts sound should be working!


Basically a new ACPI was put out by toshiba which fixes the error it was causing when used along with ALSA. I am not much of a programmer just beginning to learn Linux so thats as much as I can say without confusing myself.

I dont know if someone else has already posted this solution, I didnt find it in my search, so thought I would post it.

Hope it helps!

---

