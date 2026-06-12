---
title: "MX510 (PS/2) Not Working At All"
date: 2005-06-06
forum: Hardware &amp; Laptops
---

### Post by ksmith on 2005-06-06
Hello,

I've seen a few posts about the MX* family of mice not working but I haven't seen a solution to the problem.

I have a MX510 using the USB -> PS/2 adapter and it doesn't work in X, at all. I've tried different protocols (ImPS/2, ExplorerPS/2, MouseManPlusPS/2) but I've had no luck.  

Below is an excerpt from my xorg.conf:
```
Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
        Option          "Device"                "/dev/input/mice"
        Option          "Protocol"              "ExplorerPS/2"
        Option          "ZAxisMapping"          "4 5"
EndSection
```
I'd rather not go USB but has anyone had any luck getting an MX510 working as a PS/2 mouse?

Thanks,
Kyle

---

### Post by Juippisi on 2005-06-08
Try changing the "/dev/input/mice" to "/dev/psaux". And if that isn't working, then do "ls /dev/input" and try changing "psaux" to "input/eventX"

---

### Post by PhilippWollermann on 2005-06-08
[QUOTE=ksmith]I'd rather not go USB but has anyone had any luck getting an MX510 working as a PS/2 mouse?[/QUOTE]
Why don't you want to attach the mouse using USB? I can't think of a reason, why PS/2 should be better - if you only want to use it in Linux, that is. If you happen to dual-boot to DOS, PS/2 is really better. ;) If I remember correctly, the mouse cursor even moves smoother, when attached using USB..

---

### Post by I3roknI3ottle on 2005-06-09
im using the mx510 (blue) attached by USB and i didnt have to do anything for it to work in Ubuntu.  :razz:

---

