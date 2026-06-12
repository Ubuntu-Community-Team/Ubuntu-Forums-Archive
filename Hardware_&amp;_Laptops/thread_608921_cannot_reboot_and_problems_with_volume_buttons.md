---
title: "cannot reboot and problems with volume buttons ?"
date: 2007-11-10
forum: Hardware &amp; Laptops
---

### Post by pedor on 2007-11-10
I have installed ubuntu 7.10 on my HP nc8230 this works fine apart from two small things.

1 The volume buttons  work but only for the headphone how can I switch so they control the laptop-speakers?  And the diode on the mute button doesn´t light when it is activated .  
2 Ubuntu can shutdown but not reboot. When the system closes down it doesn´t restart  so I must press the power button to turn it off and then on again.

Where to look to solve the problems?

---

### Post by pedor on 2007-11-16
1  Now I solved with gconf-editor I add the value "Master" for /desktop/gnome/sound/default_mixer_tracks parameter
2 remain, ACPI bug ?:confused:

---

### Post by WastingBody on 2007-11-16
1: I had the same problem. To fix it I opened the preferences for the volume control and found which device my speakers were and selected that one to be controlled, or if you want you can select all of them.

---

### Post by Trevorius on 2007-11-16
I've been having problem 2 as well. The comp reboots if it's system initiated (like after an update), but not if I request it myself...

---

