---
title: "After working fine, USB device stops working"
date: 2016-04-03
forum: Hardware
---

### Post by Edward_Fish on 2016-04-03
I own a GB USB Smart Card from EMS. It's basically used for putting Game Boy ROMs on and loading into a real Game Boy. The software required is Windows only, so I run XP in a VM (virtualbox). It all works fine.
Sometimes, the software running in the VM reports an error part way through transferring ROMs and says the device is disconnected. VirtualBox does not see that the device is connected, and neither does the command *lsusb*. When this happens, I have to restart Ubuntu to make it work again. This is quite annoying and may damage the card, making it unusable.
If anyone knows why this has happened, and how to make it not happen, or even how to reconnect the card without having to reboot, help would be greatly appreciated!

Quick facts:

[LIST]
[*]Unplugging and re-inserting does not change anything.
[*]It is *not* a faulty USB cable.
[/LIST]
  
[LIST]
[*]I do not know whether the problem is caused by the software in the VM mucking it up, or Ubuntu ignoring the device partway through a transfer.
[/LIST]

---

