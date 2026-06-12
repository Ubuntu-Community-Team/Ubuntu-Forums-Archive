---
title: "Windows 7 Beta boot flag trouble"
date: 2009-01-11
forum: Installation &amp; Upgrades
---

### Post by jacobmh on 2009-01-11
I have a triple boot with Ubuntu, Vista, and Windows 7.

The menu organization, when the grub boot flag is enabled, looks like this:

Grub Menu
Ubuntu-> boots ubuntu
Windows -> Win7 boot menu with Vista and 7 -> boots either windows

I have the boot flag set to the Ubuntu partition in Gparted. Unfortunately, whenever I select Windows from the grub menu and then select Windows 7 to boot from the resulting Windows boot menu, Windows disables the grub boot flag from the ubuntu partition, causing only the Windows boot menu to appear upon reboot. 

I apologize if this is an old question by now, but how can I get either Windows 7 to STOP reassigning the boot flag, or else make Grub impervious to Windows 7's attempts to do so?

---

### Post by caljohnsmith on 2009-01-11
It sounds like your problem might be a simple issue of having the "makeactive" line the Grub menu.lst entry for Windows. How about opening your menu.lst:
```
gksudo gedit /boot/grub/menu.lst
```
Find the Windows boot entry, and if it has a "makeactive" line, delete it. That should solve your problem I think.

---

### Post by jacobmh on 2009-01-12
Will try, thanks. Last resort, I could use the Windows 7 bootloader and add in Ubuntu, which I know how to do. I just like Grub better cause it's more flexible.

---

