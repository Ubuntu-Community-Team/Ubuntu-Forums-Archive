---
title: "USB mouse not detected"
date: 2009-09-28
forum: Hardware
---

### Post by srbharadwaj on 2009-09-28
Hi,

My USB mouse dos'nt work in Ubuntu9.04,installed via Wubi in Windows
The touchpad works perfectly, also pendrives are detected correctly on the USB port but mouse is not getting detected

srb@ubuntu:~$ modprobe psmouse
srb@ubuntu:~$ xsetpointer -l
0: "Virtual core pointer"	[XPointer]
1: "Virtual core keyboard"	[XKeyboard]
2: "AT Translated Set 2 keyboard"	[XExtensionKeyboard]
3: "Video Bus"	[XExtensionKeyboard]
4: "Macintosh mouse button emulation"	[XExtensionPointer]
5: "PS/2 Mouse"	[XExtensionPointer]
6: "AlpsPS/2 ALPS GlidePoint"	[XExtensionPointer]
7: "HID 413c:8157"	[XExtensionKeyboard]
srb@ubuntu:~$

help pls....:confused:

---

### Post by nixscripter on 2009-10-03
You don't need the PS/2 driver, but the HID driver for a USB mouse.

Here is how you set everything up:

[http://www.linux-usb.org/USB-guide/x194.html](http://www.linux-usb.org/USB-guide/x194.html)

Hope this helps.

---

