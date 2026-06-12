---
title: "Dual Boot Windows/Ubuntu - Keyboard Failure on boot up"
date: 2012-08-27
forum: Hardware
---

### Post by meddyuk on 2012-08-27
Good Morning,

I  have a Dell Pc, which has Ubuntu Natty 11.04 dual booted with Windows vista. It has run fine before and i used to access the grub menu with no problems to access both OS's.

Suddenly without reason, when i boot up i now get 'keyboard failure' after the BIOS splash and i am unable to use the keyboard up and down arrows to access the grub menu. Once Ubuntu has booted up the keyboard is fine again.

Is all lost? I know i can alter the grub boot sequence to make windows boot up first, but how then do i access ubuntu? Do i have to choose which OS to run with?

Meddy.

---

### Post by ahallubuntu on 2012-08-27
Is this a USB keyboard?  If so, look in the BIOS for setting related to "legacy USB" support.  Also, unplug all other USB devices.  You can even try resetting your CMOS (BIOS) settings to default settings.  On a Dell, the F2 key while you are powering up should get you into BIOS Setup.

Otherwise, look around in BIOS Setup while you are in there - maybe there's some other option that could fix that.

---

