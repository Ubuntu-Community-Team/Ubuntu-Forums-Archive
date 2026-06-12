---
title: "USB Mouse Not Working"
date: 2008-05-15
forum: Hardware
---

### Post by chr3681 on 2008-05-15
Okay... I have a standard Microsoft USB Optical mouse. When I plug it in to the USB port, the mouse lights up for a second, and then that's it. It does not work at all, it works on other computers so it's not the mouse and the USB port is fine because when I had my windows drive in, the mouse worked fine. I'm running Hardy on an Acer Aspire 5000.

Thanks in advance for your help!

Chris

---

### Post by hermes0710 on 2008-05-16
Have the mouse unplugged and run from a terminal ```
 sudo dmesg -c
```
Then plug in the mouse again and after it messes up, run ```
dmesg
``` in terminal and post the output

---

### Post by alex sun on 2008-05-21
The same problem.
dmesg returns nothing.
A mouse worked fine in Gusty 64.
It doesn't work in Hardy 64.
Some mouses flash on connection, some don't.
USB flash cards work fine both Gusty 64 and Hardy 64.

---

### Post by chr3681 on 2008-05-21
I wish I could help you but all I did was run updates and mine magically started working... hopefully someone else will be able to help. I marked the thread as unsolved so you will get better responses!

---

