---
title: "UDEV y FXLOAD"
date: 2008-04-08
forum: Hardware &amp; Laptops
---

### Post by alan888 on 2008-04-08
Hi all:

I have a GPIB adapter (ni_usb_b) and I'm trying to use it with ubuntu (gutsy gibbon). I installed the package ...linux-gpib-3.2.10 and I followed all the instruction, to the line that refers to fxloader. The istruction is (the example in the README file):

**[COLOR="Navy"]fxload -D /proc/bus/usb/001/002 -I niusbb_firmware.hex -s niusbb_loader.hex[/COLOR]**

I list the directory (**[COLOR="Navy"]ls /proc/bus/usb/[/COLOR]**) and...nothing inside...nooooooooo. (all of this command with the adapter plugged and recognized by lsusb). Obviusly the command return me some problems with the device and ....

What I must do for finish the installation of my GPIB-adaptor?
How I could load the new firmware of the adaptor?
It's somthig with udev and fxload or should be function?

Thanks.-

---

### Post by domoikane on 2008-05-06
Hello, i'm a newbie, but have you tried /dev/bus/usb/001/002, it seems that this is for new versions of ubuntu.

---

