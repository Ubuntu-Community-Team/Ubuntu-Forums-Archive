---
title: "[SOLVED] &amp;quot;Mode Not Supported&amp;quot; when booting w/ new LCD monitor and fresh install 8.04"
date: 2008-12-08
forum: Installation &amp; Upgrades
---

### Post by gnoel on 2008-12-08
_The setup:_

I attached a new widescreen monitor (1920 x 1200 @ 60 Hz) to an existing installation running Edgy (6.10) and it booted fine with no configuration changes.  The computer is an old Gateway 933 mHz with 512 RAM and a crappy ATI video card.  It's no speed demon, but it has been running very reliably since Edgy was installed over 1.5 years ago.

Another computer recently installed with Hardy (8.04) booted fine on the same monitor.

I did a fresh install of 8.04 from the Live CD (checked with md5sum) on top of Edgy (no dual boot).

_The problem:_

After POST and after GRUB runs, the monitor (a Samsung T240) displays a "Mode Not Supported" warning in a message box.  This message box drifts about 1/8th of the way down the screen for about a minute, then the Ubuntu login screen starts to appear in a broken fashion for a few seconds, then finally appears.

Login is normal, and after that the screen behaves normally and looks great at a resolution of 1600 x 1000.

Is there some sort of default screen setting at boot time that is causing this?  If so, where can I find this?  This is not trivial, my wife really hates this new "feature."

Thanks for your help!!!

---

### Post by gnoel on 2008-12-08
A coworker pointed me to the possibility that I might have to reset the default screen resolution in GRUB.  Some more searching revealed the following thread where this is discussed:

[http://ubuntuforums.org/showthread.php?t=258484&highlight=grub+resolution]("http://ubuntuforums.org/showthread.php?t=258484&highlight=grub+resolution")

Short answer: edit /boot/grub/menu.lst and add "vga=0x342" (or another hex value to represent the resolution you want) to this line:

kernel /boot/vmlinuz-2.6.15-27-386 root=/dev/hda3 ro quiet splash vga=0x342

Case closed.

---

