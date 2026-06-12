---
title: "ps/2 mouse not recognised in 11.04"
date: 2011-06-13
forum: Hardware
---

### Post by icodemonkey on 2011-06-13
hey all 
had a usb mouse as the default one but it died so pluged in a ps/2 mouse but now it wont recognise it has a mouse connected.
any one solved this problem?
--------------------------------
or what file(s) need to be edited to get it running it?
it shows up as /dev/ttyS0

---

### Post by icodemonkey on 2011-06-13
*bump*

---

### Post by crispy_420 on 2011-06-13
Did you turn off the system before installing or reboot since PS/2 is not hot swappable?

---

### Post by icodemonkey on 2011-06-13
knew that turned system off, plugged in mouse, you know the rest but the mouse pointer just sits there no matter how much you move the mouse or how many reboots you do.

---

### Post by crispy_420 on 2011-06-13
Is it an optical mouse? Does it work in other operating systems?

If so, does it light up before the OS starts up?

---

### Post by icodemonkey on 2011-06-13
not an optical but an old style trackball and yes it works with win and shockingly ubuntu 6.10

---

### Post by crispy_420 on 2011-06-17
Do you have a PS/2 to USB adapter laying around? Maybe try that?

---

### Post by icodemonkey on 2011-06-17
dont have ps/2 - usb adapter but something new has been added.
using this command ```
xsetpointer -l | grep Pointer

```i get this 
```
2: "Virtual core pointer"    [XPointer]
4: "Virtual core XTEST pointer"    [XExtensionPointer]
9: "Microsoft Microsoft&#65533;&#65533; Digital Media Keyboard 3000"    [XExtensionPointer]
11: "PS/2 Generic Mouse"    [XExtensionPointer]

```
so it can see the trackball but not use it the pointer is stuck in the bottom right of screen

---

