---
title: "NVIDIA GT 330M: Cannot change brightness"
date: 2010-12-29
forum: Hardware
---

### Post by Quadunit404 on 2010-12-29
I have a Samsung NP-RF510 laptop and while I have been able to resolve the keyboard and touchpad issues that seems to plague installing Linux on a Samsung laptop [thanks to this thread]("http://ubuntuforums.org/showthread.php?t=1628673") I am still experiencing problems regarding the ability to change the brightness. The ability to change the brightness is still there, just not functional.

Any other owners of a GT 330M able to help me? Changing the brightness is rather necessary due to my family's tendency to travel frequently and because I bring my laptop to school to do work on it and while the brightness dims when the laptop is unplugged and running on battery power it does not when it's plugged in after feeding off the battery for an amount of time.

---

### Post by Kramer2010 on 2010-12-29
This may work...

In terminal:

sudo gedit /etc/default/grub

Change the line GRUB_CMDLINE_LINUX="" into GRUB_CMDLINE_LINUX="acpi_osi=Linux"

sudo update-grub

Restart your linux

---

### Post by Quadunit404 on 2010-12-30
Since I use Burg (which is Grub except fancier) I did what you told me, only with the appropriate Burg commands. Gonna restart and see if that worked.

Nope, didn't do a thing. Still have no brightness control.

---

### Post by Quadunit404 on 2011-01-04
FIXED IT! I put this:
```
    Option         "RegistryDwords" "EnableBrightnessControl=1"
```
in my xorg.conf in the section that identifies my graphics card. Now brightness works perfectly.

---

### Post by kwikshot on 2011-06-16
Can you post your xorg.conf please? I can't get it to work and I have tried it in each section of my xorg.conf that has anything to do with the graphics card.

Also, the "Dont zap" option to enable the ctrl-alt-backspace shortcut doesn't seem to be working either...

---

### Post by kwikshot on 2011-06-22
Bump

---

### Post by avaneesh_pathak on 2011-09-25
> **Kramer2010 said:**
> This may work...

In terminal:

sudo gedit /etc/default/grub

Change the line GRUB_CMDLINE_LINUX="" into GRUB_CMDLINE_LINUX="acpi_osi=Linux"

sudo update-grub

Restart your linux

I love you man!!!!:p
I tried everything, your solution so simple, yet got the output
Thanx bro!

---

