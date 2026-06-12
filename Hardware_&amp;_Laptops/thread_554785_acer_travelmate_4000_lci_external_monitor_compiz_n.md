---
title: "acer travelmate 4000 lci external monitor compiz no image"
date: 2007-09-19
forum: Hardware &amp; Laptops
---

### Post by jeezus84 on 2007-09-19
evening everyone,

I installed Unbuntu 7.04 on my laptop using my external monitor. I got Compiz all set up and working nicely. While working with my external monitor my laptop screen would display a red background and nothing else.

Then one day, I tried booting Ubuntu with the external monitor unplugged. Ubuntu goes through the boot process (orange progress bar) then the screen dissappears. I hear the bootup sound then nothing. If I hit CTRL+ALT+Backspace X restarts but then goes back to a blank screen.

So I tried going back and booting with my external display attached to no avail. My external monitor displays a blank screen as well.

So, how would I go about getting my laptop monitor to be my primary and only display? I don't want to mess around with my external monitor until I get my laptop screen working under Ubuntu again.

Thanks for your help.

---

### Post by jeezus84 on 2007-09-19
fixed it.

just run `sudo dpkg-reconfigure -phigh xserver-xorg` and restart X.

---

### Post by jeezus84 on 2007-09-19
fixed it.

just run `sudo dpkg-reconfigure -phigh xserver-xorg` and restart X.

---

