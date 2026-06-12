---
title: "display driver problem?"
date: 2007-08-09
forum: Hardware &amp; Laptops
---

### Post by stlouis1 on 2007-08-09
well...i was having some problems running opengl games.....so i tried to remove the nvidia-glx-new and installed the old nvidia-glx

anyway, when i rebooted, i got a black screen with a cursor.

so what i tried so far, was removing the nvidia stuff, kernel modules and glx

and then tried to reconfigure xorg. and it actually just rebooted to the gui after that while i was typing....

im gonna try and reinstall the nvidia drivers now, guess ill post back if i have any problems

---

### Post by stlouis1 on 2007-08-09
well, when i reinstalled the driver, it crashed on me again....so i redid the removal and reconfigured xorg again.

i used the envy script to install the nvidia drivers and thats working fine

but i still cant run anything that uses opengl

---

### Post by stlouis1 on 2007-08-09
nvm, i fixed it. i ran the nvidia settings panel as root and save the xorg configuration there and rebooted, its working beautifully now

---

