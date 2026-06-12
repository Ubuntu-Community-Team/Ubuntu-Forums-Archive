---
title: "Keyboard not work on boot"
date: 2014-12-07
forum: Hardware
---

### Post by ivan66 on 2014-12-07
My microsoft wired usb keyboard not working in BIOS  and GRUB after Ubuntu 14.04 shut down, but it works after booting windows 7
How to make it work after Ubuntu shutdown?

---

### Post by Bashing-om on 2014-12-07
ivan66; Hi ! Welcome to the forum.

Check your bios settings for USB devices and change the setting. As the keyboard works after ubuntu is started, one is looking at what drivers that bios hands off to the boot code, so that grub ( Grand Unified Bootloader) adjusts.

Also ensure that "plug and play" is enabled.

[INDENT][INDENT]all in the process
[/INDENT][/INDENT]

---

