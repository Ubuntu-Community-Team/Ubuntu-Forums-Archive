---
title: "Touchpad doesn't work"
date: 2015-06-10
forum: Hardware
---

### Post by darthredskin on 2015-06-10
I fresh installed Ubuntu 14.04 yesterday on my Gigabyte P35W laptop, during the install process I was able to use my touchpad. However, once Ubuntu was fully installed it stopped working, in fact the cursor didn't even show up. I googled many solutions and options, yet none of them work, I was able to get my cursor to re-appear though.


I had Ubuntu installed on my old laptop and it worked right out of the box, no issues. I'm not sure if it's the touchpad brand (Synaptics) or if it's something I'm missing, but I feel I've tried everything.


And yes I tried "sudo modprobe psmouse" and various variations of that command to no avail and I don't have an external mouse.

Also I noticed, the sound doesn't work unless I plug in headphones.


Any help or suggestions would be greatly appreciated. Thank you.

---

### Post by Pilot6 on 2015-06-12
Please add output of

xinput
dmesg | grep pnp

terminal commands.

---

