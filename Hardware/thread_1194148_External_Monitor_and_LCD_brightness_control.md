---
title: "External Monitor and LCD brightness control"
date: 2009-06-22
forum: Hardware
---

### Post by the jaq on 2009-06-22
I have a 5 year old toshiba Satellite M35-S456 with a GeForce 5200 Go. I have been trying to use the 1280x800 laptop display with an external Dell 1650x1080 in either Twin View or as separate X screens.


1. The external monitor must be plugged in to the machine (via VGA) at boot or it will not work. Nvidia-settings recognizes the display if it is plugged in afterward, but I cannot get it to display anything.

2. Without the external monitor the LCD display works fine. The Toshiba ACPI driver is installed and the LCD brightness works fine, i.e. echo "brightness:7" >  /proc/acpi/toshiba/lcd or via hotkeys through fnfxd.

The problem arises when I want to run both monitors. The external monitor is plugged at boot and the machine uses it as the default display. After logging in, xorg.conf turns the native laptop LCD on and it works in twin view or as a separate x screen, but it is stuck at the lowest brightness and is unusable!!

I can update the brightness value but the screen doesn't respond to changes in the brightness. I notice that /proc/acpi/toshiba/video lcd_out = 0, but the value doesnt change when I ask it too. Similarly, crt_out = 1 and it will not change.

Any advice? :confused::confused: I desperately need the extra resolution!!

---

### Post by the jaq on 2009-06-23
:confused:

---

### Post by diediaga on 2009-07-01
hi I have exactly the same problem
I desperate need a solution for that
did you find out it?

---

### Post by the jaq on 2009-07-14
I have no solution. I use the laptop display only to show PDFs with white background. :lolflag:

---

### Post by diediaga on 2009-07-15
hi
I found the solution for my laptop
what I did is to change some parameters in the BIOS.
I don't have the laptop here with me and I don't remember exactly what I change. Also any BIOS is different.
but you can look in the section of VGA-LCD displays and change the priority of it.
I hope it could help you.

regards
diego diaz

---

### Post by the jaq on 2009-07-15
Amazingly simple... In my Toshiba bios I have a setting: "Select Display." I changed from auto-select to LCD+Analog RGB with miraculous results.

Thanks.

---

### Post by diediaga on 2009-07-15
good !!
I am happy you have solvent your problem also.
so, please could you change the title of this post adding [Solved] so other people can find it.
:p

---

