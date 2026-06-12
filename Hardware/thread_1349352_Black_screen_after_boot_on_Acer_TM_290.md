---
title: "Black screen after boot on Acer TM 290"
date: 2009-12-08
forum: Hardware
---

### Post by phreak-1 on 2009-12-08
Hi,

I just finished installing Ubuntu 9.10 on an old Acer TM 290. And just like described in  [this thread]("http://ubuntuforums.org/showthread.php?t=1326129") or at [superuser.com]("http://superuser.com/questions/68122/bios-corrupted-how-to-proceed-acer-travelmate-290") i get a black screen after booting (right after grub).

It is just a display problem since the startup sound plays after a short while. I am also able to boot the laptop using an external screen and then unplugging it once it has booted.

The solutions I have tried so far:

[LIST]
[*]Pressed FN+F5
[*]Added 'vga=711 noapic nolapic' to the grub default params
[*]Updated to the latest available firmware
[*]Unplugging the battery and power supply and swapping ram
[/LIST]

any suggestions?

cheers
maros

---

### Post by phreak-1 on 2009-12-09
I have played around with the various framebuffer params (as described at [http://www.mjmwired.net/kernel/Documentation/fb/intelfb.txt](http://www.mjmwired.net/kernel/Documentation/fb/intelfb.txt)) but this has lead nowhere yet.

One more observation I have made:
When I boot with an external screen, the laptop screen works properly. The laptop screen continues working when I unplug the external screen, but once i start the display system settings the whole system freezes. However if I leave the external screen connected the display settings work fine.

Cheers

---

