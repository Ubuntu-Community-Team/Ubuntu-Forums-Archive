---
title: "G555 Touchpad detected as PS/2 Mouse"
date: 2011-01-21
forum: Hardware
---

### Post by juanfpina on 2011-01-21
When I installed Ubuntu 10.10 I had various problems, the speakers and headphone jack, the screen, and other little things. After about a month of reading and learning I've fixed everything but two things. The touchpad is detected as "PS/2 Mouse" so I don't have the touchpad tab in Mouse Settings, and the mic doesn't work. I got the headphone jack and speakers to work by editing alsa-base.conf, but could never get the mic working. The touchpad is Alps by the way.

Does anyone have any solutions to these two problems?
Thanks :)

---

### Post by Gagandeep_1985 on 2011-01-22
i didn't installed ubuntu but i tried it from the CD. my touchpad doesn't working. not a single move.. hoe will i fix it...??  please help me out.....

thanks

---

### Post by dtox77 on 2011-02-23
I have the same problem with an Acer 3820T. The touchpad (ALPS) is recognized as a standard PS2 mouse. The touchpad is OK for moving the cursor around, but for emulating mouse buttons with the touchpad it's worthless. The pad is working excellent in Windows 7.

To get the scrolling working I had to add:
options psmouse proto=imps
to
/etc/modprobe.d/psmouse.conf

Anyone found a fix for the ALSA touchpads yet?

---

### Post by juanfpina on 2011-02-23
> **dtox77 said:**
> I have the same problem with an Acer 3820T. The touchpad (ALPS) is recognized as a standard PS2 mouse. The touchpad is OK for moving the cursor around, but for emulating mouse buttons with the touchpad it's worthless. The pad is working excellent in Windows 7.

To get the scrolling working I had to add:
options psmouse proto=imps
to
/etc/modprobe.d/psmouse.conf

Anyone found a fix for the ALSA touchpads yet?
I just did this and it didn't work at all. I've tried all the proto=??? rules and none will work.

---

