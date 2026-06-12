---
title: "Working Ubuntu USB stick not booting successfully on a HP t573o Thin Client"
date: 2009-06-23
forum: Hardware
---

### Post by XYZ1 on 2009-06-23
Hi,
I used the "uSbuntu live creator" (screenshot see here: [http://imag.malavida.com/mvimgbig/download/usbuntu-live-creator-5702-1.jpg](http://imag.malavida.com/mvimgbig/download/usbuntu-live-creator-5702-1.jpg)) to create an Ubuntu USB stick.

In "uSbuntu live creator" I selected the following options:
- Format the key in FAT32
- I took the whole 2GB of the USB Stick for Persistance

Then I created the USB Stick.
It's booting and working fine on a regular PC.


But then I tried it on an HP t5730 Thin Client but during boot I'm getting the following message and the boot process stops:

[FONT="Courier New"][COLOR="Blue"]Begin: Loading essential drivers... ...
Done.
Begin: Running /scripts/init-premount ...
Done.
Begin: Mounting root file system... ...

BusyBox v1.10.2 (Ubuntu 1:1.10.2-2ubuntu7) built-in shell (ash)
Enter 'help' for al ist of built-in commands.

(initramfs) _[/COLOR][/FONT]


This happens only on the Thin Client, regardless if I choose the Live or the Persistant mode.


Any idea?

---

### Post by XYZ1 on 2009-06-24
Hi,
in the meantime I tried to unplug all other USB devices (mouse and keyboard). But it's still not booting.
I also waited a couple of minutes as soon as the (initramfs) message appeared but it's still not working :(

Does anybody have any idea what I can do?

---

