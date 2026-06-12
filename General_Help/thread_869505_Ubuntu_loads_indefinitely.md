---
title: "Ubuntu loads indefinitely"
date: 2008-07-24
forum: General Help
---

### Post by Lovok on 2008-07-24
Every now and then, when I boot Ubuntu Hardy Heron, it will get to the loading screen and load indefinitely.
The tiny bar goes from left to right until I reboot. Normally after a reboot, I get in just fine, sometimes it takes two.

Happens often when I boot from XP into Ubuntu (using the BIOS to change the hdd priority list, not technically dual booting)
Happens often when I stop hibernating/suspension.

Normally a reboot solves this.

Any reason why this happens?

Thanks.

---

### Post by overdrank on 2008-07-24
> **Lovok said:**
> Every now and then, when I boot Ubuntu Hardy Heron, it will get to the loading screen and load indefinitely.
The tiny bar goes from left to right until I reboot. Normally after a reboot, I get in just fine, sometimes it takes two.

Happens often when I boot from XP into Ubuntu (using the BIOS to change the hdd priority list, not technically dual booting)
Happens often when I stop hibernating/suspension.

Normally a reboot solves this.

Any reason why this happens?

Thanks.

Hi and have you tried to remove the quiet splash from the kernel line so you can see any errors?
When booting highlight the OS you want to boot and then press the esc key and then on the kernel line press e to edit remove the quiet splash then b to boot.
Or you may try the ctrl, alt, F1 keys when ubuntu is booting to see any errors.

---

### Post by Lovok on 2008-07-27
I ended up installing the 64bit version, without Edubuntu, and I managed to catch the error without the quiet splash

```
/built/buildd/linux-2.6.24/drivers/hid/usbhid/hid0cpre.c:v2.6:USB HID core driver
```
and then 30 seconds later
[code]ata3.00 : qc timeout ([code/]
There was something in that parenthisis, but the bootup resumed. It seems to get stuck around the same place it boots up my mouse, Logitech MX518.
It seems less frequent without the quiet splash...

---

### Post by tom66 on 2008-07-27
If it's a USB mouse problem, could you try it with another one or a PS/2 mouse (standard pin connector)?

---

