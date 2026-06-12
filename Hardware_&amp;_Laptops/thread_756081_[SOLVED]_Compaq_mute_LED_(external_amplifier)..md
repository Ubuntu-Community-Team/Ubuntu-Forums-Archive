---
title: "[SOLVED] Compaq mute LED (external amplifier)."
date: 2008-04-15
forum: Hardware &amp; Laptops
---

### Post by Kinst on 2008-04-15
Hi. Muting works, but the LED for the mute button is connected to the external amplifier setting. Can I make it so pressing the mute button turns off the external amp?:rolleyes:

---

### Post by Kinst on 2008-04-15
K I sort of answered my own question.

Copy this into /etc/modprobe.d/sound, or possibly /etc/modprobe.d/options:

> options snd-atiixp ac97_quirk=7

Then restart and the light will work. :)

---

