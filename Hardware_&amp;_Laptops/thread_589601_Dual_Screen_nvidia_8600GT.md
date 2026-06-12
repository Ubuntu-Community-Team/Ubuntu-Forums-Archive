---
title: "Dual Screen nvidia 8600GT"
date: 2007-10-24
forum: Hardware &amp; Laptops
---

### Post by ndroo on 2007-10-24
Hey,

I've got a nvidia 8600GT installed in my desktop PC. I normally have dual screens setup, but i dont have the slightest as to how to get this working.

Ive read a lot on the forum, but so far...im still confused. This is my first serious attempt at converting from windows to linux (and its been good so far, laptop went across very smooth - and this is my only issue with the desktop).

Not a huge issue, but as a developer i like dual screens...so the sooner i get it running the sooner im feelin nif-tay :)

Thanks guys,

- Andrew

---

### Post by enigma_0Z on 2007-10-24
Have you already installed the nvidia-glx driver (or installed the drivers from nvidia's website)?

If so, then it should be a matter of just plugging your monitor up and going to the nVidia X Server Settings app.

That program should be under "system" in the menu. If you can't find it there, open a console/terminal and run "nvidia-settings"

From there, go to "X Server Display Information" and enable your second monitor (select twinview). From there, position the monitors like you like them and hit apply.

If that works, then I can help you out with a more permanent configuration (if you're up for it)

---

### Post by earobinson on 2007-10-24
yup, once you have the ristricted drivers installed (ubuntu should do this for you) dual screen is a ```
sudo nvidia-settings
``` and X reset away.

---

