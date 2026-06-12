---
title: "Laptop Brightness"
date: 2009-01-14
forum: Hardware
---

### Post by studentidiot on 2009-01-14
The brightness on my Vaio FZ340e/b doesn't work. (And the same for even older vaios and another brand laptops using the same graphics card It sucks the power out of the battery and hurts my eyes. I've been hoping this would be fixed for a year and a half. Is this going to be fixed in 9.04?

Is there ever going to be better power manangement control in Ubuntu? Ubuntu works great on desktops (sorta), but seems very behind on laptops..

---

### Post by utnubuuser on 2009-01-14
Hi  --  contact the manufacturer and request native support for linux.

---

### Post by studentidiot on 2009-01-14
> **utnubuuser said:**
> Hi  --  contact the manufacturer and request native support for linux.

There already is.

Nvidia 8400M GS.

---

### Post by utnubuuser on 2009-01-15
Vaio is this not working?

---

### Post by igknighted on 2009-01-15
> **studentidiot said:**
> There already is.

Nvidia 8400M GS.

Most of the power management features are not in the graphics card.  They are ACPI functions, and acpi is usually a tightly-bundled, proprietary thing built into the bios by the manufacturer.  Sony is notoriously bad for not making specs available to open-source devs.

Also, is your problem the hotkeys, or the actual dimming itself.  You can manually dim the screen from the control panel (or the proper text file if you prefer) if the hotkeys simply don't work.

---

### Post by studentidiot on 2009-01-23
> **igknighted said:**
> Most of the power management features are not in the graphics card.  They are ACPI functions, and acpi is usually a tightly-bundled, proprietary thing built into the bios by the manufacturer.  Sony is notoriously bad for not making specs available to open-source devs.

Also, is your problem the hotkeys, or the actual dimming itself.  You can manually dim the screen from the control panel (or the proper text file if you prefer) if the hotkeys simply don't work.

That information is available. That information has been reverse engineered posting on the bug report for this, and other laptops.

Ubuntu knows I'm pressing the hotkeys. It displays the bar. The brightness just doesn't chaange. Dimming from control panel doesn't work.

---

### Post by studentidiot on 2009-01-24
> **studentidiot said:**
> That information is available. That information has been reverse engineered posting on the bug report for this, and other laptops.

Ubuntu knows I'm pressing the hotkeys. It displays the bar. The brightness just doesn't chaange. Dimming from control panel doesn't work.

bump

---

### Post by studentidiot on 2009-01-25
bump

---

### Post by Rendrago on 2009-01-25
You could try xbacklight.

```
sudo apt-get install xbacklight
```

Then:

```
xbacklight = 100

or 

xbacklight = 50
```

Or try:

[https://help.ubuntu.com/community/SonyVaioBrightness](https://help.ubuntu.com/community/SonyVaioBrightness)

---

