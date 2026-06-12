---
title: "Logitech Wave Keyboard &amp; Mouse"
date: 2008-11-24
forum: Hardware
---

### Post by Electrovellum on 2008-11-24
This is nothing to do with special keys - just the standard keys and Grub failing to dual boot correctly: 

Using dual boot Vista 64 & Ubuntu 8.10 with a Microsoft Wireless keyboard & mouse everything is fine - not worried about special keys at this stage. 

Connecting a Logitech Wave wireless keyboard and mouse works fine in Vista, then if I reboot (Grub dual boot menu) the keyboard works ok whilst the BIOS is loading (ie it is possible to use arrows & alpha keys to alter CMOS BIOS settings) but once under control of Grub, the Logitech keyboard is dead. 

At this stage the Grub menu times out & Ubuntu loads. After a short delay of perhaps 1 to 2 seconds (not present with the Microsoft keyboard & mouse), both keyboard & mouse operate normally in Ubuntu. 

A restart from here repeats the action above, ie it is impossible to select Windows (4th item on selection menu, needing arrow key use) and the menu times out into Ubuntu. At this stage all I can do in order to get into windows is to swap keyboards back to the Microsoft keyboard, when the Grub dual boot works perfectly. A hot swap back to the Logitech keyboard works fine with the Windows special key definitions still operative, and the cycle repeats as above. 

Looks like a problem in Grub, not handling keyboard correctly - any ideas?

---

