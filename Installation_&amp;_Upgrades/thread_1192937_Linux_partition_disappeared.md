---
title: "Linux partition disappeared?"
date: 2009-06-20
forum: Installation &amp; Upgrades
---

### Post by Zorrorrorro on 2009-06-20
Hi all, 

Thank you for your help in advance.

I had edited /boot/grub/menu.lst to have Windows XP as the default OS. There was an update to run in Ubuntu 9.04 and it asked about my edited menu.lst. Without thinking I just clicked on (install main something....) which would basically overwrite it with the default Linux menu.lst... which doesn't include Windows!

So GRUB was booting up but obviously could no longer find the partition to Windows.

So I booted to the windows CD to fix the MBR and now GRUB is gone. I can at least get intow Windows now, but the Linux GRUB options are now gone.

How do I restore the original GRUB menu?

Thank you!

Zorrorrorro

---

### Post by presence1960 on 2009-06-20
all you needed to do was edit the menu.lst file to include Windows. it is too late for that now. do this:
```
1. Boot your computer up with Ubuntu CD
2. Open a terminal window or switch to a tty.
3. Type sudo grub. Should get text of which last line is grub>
4. Type "find /boot/grub/stage1". You'll get a response like "(hd0,1)". 
   Use whatever your computer spits out for the following lines.
5. Type "root (hd0,1)", or whatever your hard disk + boot partition 
   numbers are for Ubuntu.
6. Type "setup (hd0)", to install GRUB to MBR, or "setup (hd0,1)" or 
   whatever your hard disk + partition # is, to install GRUB to a 
   partition.
7. Quit grub by typing "quit".
8. Reboot and remove the bootable CD.
```

if windows and Ubuntu are on the same drive in #6 use setup (hd0).

---

