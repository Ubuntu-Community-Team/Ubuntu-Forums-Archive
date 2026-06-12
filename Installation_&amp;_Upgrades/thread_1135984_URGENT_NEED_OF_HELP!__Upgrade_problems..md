---
title: "URGENT NEED OF HELP!  Upgrade problems."
date: 2009-04-24
forum: Installation &amp; Upgrades
---

### Post by jimmyboy09 on 2009-04-24
I think my situation necessitates that I list all of the details:

- A LOT OF INFO BUT PLEASE HELP ME...

- I upgraded from intrepid to jaunty via synaptic.  During the process I chose to **KEEP** my _menu.lst_ and something about _read-aheads_.

- After restart, Grub only shows the options to boot from intrepid (kernel 2.6.27-11-generic) and my xp partition.  _NO_ signs of jaunty at all.

- With no other options, I boot from what it calls the intrepid (8.10) partition.

- Grub selects the ubuntu partition and begins to boot.  Bootsplash continues.  After bootsplash finishes, I get a BLANK SCREEN.  Nothing else happens, and I'm forced to restart.

- From Grub, I manually change the kernel name / initrd stuff by pressing the 'e' key, and I get the same result.  Blank screen.

- From other suggestions, I booted into recovery mode, and ran as root.  As root, I backed up menu.lst and made a new one.  Now grub shows the correct kernel name at startup.  BUT since menu.lst was updated, my xp partition doesn't show up as a choice anymore!  Boot from ubuntu partition.  Blank screen after bootsplash.  

- Does anyone know how I can boot up my windows partition from the grub command-line or elsewhere? 

- As for saving my ubuntu partition, I figure I can boot into safe mode, backup my home dir to a usb drive from terminal, get a livecd, and do a fresh install.  **But I need to know the terminal commands to do that.**  Ewww.

- Or, if someone knows how to remedy my situation without doing a complete overhaul, PLEASE PLEASE HELP.  My computer is essentially worthless right now :(

Loads of thanks to whoever can help me...

---

### Post by jimmyboy09 on 2009-04-24
Oh, and for what it's worth:

- With intrepid I used customized GDM themes.  Does that mean with the upgrade those don't show anymore, and neither does the default one?  I may have to revert back to default gdm login screen from terminal.

---

### Post by jimmyboy09 on 2009-04-24
Please halp meh....

---

