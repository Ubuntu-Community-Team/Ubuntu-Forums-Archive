---
title: "USB ports not detected"
date: 2006-10-23
forum: Hardware &amp; Laptops
---

### Post by bettepreda on 2006-10-23
Hi! Just installed Ubuntu 6.06. I have a big problem with all the usb ports of my computer: all of them (8!) were not detected!
I checked the *lsusb* but none of them is listed. I also checked the peripheral manager: all other ports are mounted (COM etc.) except from the usb! It seems that the whole usb controller was not  detected. Could anyone help me with that?
:confused:

---

### Post by bettepreda on 2006-10-23
the output for "dmesg /grep usb" is:
Usage: dmesg [-c] [-n level] [s- bufsize]

What does this mean?

---

### Post by bettepreda on 2006-10-25
i found kleemans answer very useful (in the thread "USB Ports Not Working!"). i report it for anyone who has the same problem:

open a terminal and do this issue:
sudo gedit /boot/grub/menu.lst

"page down and
Look for a line starting with
kernel /boot/vmlinuz-2.6.10
there will be other stuff after this."
Add
acpi=off apm=on
AT THE END OF THE LINE and reboot.
it worked!!
thanks:D

---

