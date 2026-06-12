---
title: "HP 1020 Install plugin problem 9.04 AMD64"
date: 2009-04-28
forum: Hardware
---

### Post by Lemurion on 2009-04-28
I just upgraded to 9.04 and I can't get my HP Laserjet 1020 to work.

I tried uninstalling and reinstalling it but it seems to only get part way through the process.

When I run system-config-printer and look for a new printer I get the option to select a printer and pick the HP 1020.  It then tells me I need to install a plugin.  I opt to install the plugin and it drops me back to the original system-config-printer window with no printer.

If I opt not to install the plugin I get the printer but it doesn't print.

I don't want to have to reboot into Windows just to use my printer.

---

### Post by wally the duck on 2009-04-30
Welcome to the club! The hp 1020 does not work with jaunty... I've tried every 'fix' I could find, so far, and each one worked for a while. Then restart and back to square one... plus the usb mouse will not work on the restart. Unplug the USB from the printer and plug it back in and the printer reloads the firmware and all is well again. temporarily.

I'll keep trying stuff.

---

### Post by wally the duck on 2009-05-03
Still no improvement. Removed all the HP drivers, loaded fresh, sudo hp-setup.... the firmware loads perfectly, the printer works OK until the next reboot. If the printer is turned off during the reboot and started later the firmware is loaded and the printer works OK. If the printer is 'on' during boot, the lights blink to indicate that the firmware is loading, but the pattern is different. The printer then will not work and the next boot will take two or three minutes (the delay is during the bios part of boot, not the Ubuntu part, which makes me think the USB is the problem). The foo2 driver does not work at all; HP 3.9.2, 3.9.4 and 3.9.4.b all do as described above.

---

