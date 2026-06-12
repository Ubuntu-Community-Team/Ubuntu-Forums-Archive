---
title: "thinkpad 600 sound and acpi"
date: 2007-03-06
forum: Hardware &amp; Laptops
---

### Post by loumy on 2007-03-06
Hello,

I have a thinkpad 600, not 600e, not 600x (2645-450) and I have a big problem with
sound and acpi.

In this forum, I find a solution for the sound ... and it works fine !!! but I have no acpi control. 

After, I find a solution for the acpi ... and it's ok !!! but I have no sound.

If you have a solution for sound and acpi work at the same time ... I am very interesting !!!

Have a nice day

---

### Post by freshman on 2007-04-18
Hello,

I have the same problems in my 600e

I have not tested disabling of acpi, but pretty sure

Gnome does see the ALSA-mixer and OSS-mixer correctly,
I can change volume level. But when I try to open mp3
in, for instance, XMMS, it reports about problems with
sound device or possibility to such a device to be busy.

I prefer to have acpi rather then sound

---

### Post by borris.morris on 2007-05-19
do this... ```
sudo gedit /boot/grub/menu.lst
```
on the line that has "defoptions" add "acpi=force pci=noacpi" and then run ```
sudo update-grub
```
One problem, sound doesn't work after suspend.

---

