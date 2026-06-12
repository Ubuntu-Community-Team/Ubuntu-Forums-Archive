---
title: "Install Video Prob."
date: 2009-12-08
forum: Hardware
---

### Post by tvadmirer on 2009-12-08
Hi,

Newbie here.

I've just got the Karmic Koala disc included with the January 2010 edition of Linux Magazine.

I have an Acer Aspire 5738 laptop with the Mobile Intel 4 Series Express Chipset Family video set.

I'm finding that I have no video at all (X not starting?) with either the 32 or the 64 bit versions.  The sound starts up as I can hear the Ubuntu Fanfare, but no video!!!  :(

Any tips or start-up configurations?

Geoff

---

### Post by gordintoronto on 2009-12-08
I found this eventually when I searched the forums for Acer Aspire 5738:

- startup from the live cd!
- choose your language in the language menu
- press F6 for the bootparameters menu
- press esc to get back to the main menu
- type in the modeset: 'i915.modeset=0'
- press enter to start the live cd test drive

the i915 command can be also used in the grub menu, on startup hold down the shift key, you will get the list of installed kernels, just type 'e' to get into edit mode and insert the i915.modeset=0 right behind the splash quiet commands, after this just press ctrl + x to boot the machine with this setup.

---

### Post by tvadmirer on 2009-12-08
Thanks - looks as though this is working as I'm watching it boot up at the mo.

Geoff

---

