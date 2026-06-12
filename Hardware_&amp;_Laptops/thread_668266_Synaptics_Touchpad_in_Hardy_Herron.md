---
title: "Synaptics Touchpad in Hardy Herron"
date: 2008-01-15
forum: Hardware &amp; Laptops
---

### Post by Balk2K on 2008-01-15
Hi all,

I've installed Ubuntu Hardy Herron on my HP Pavilion dv1000 notebook which has a Synaptics touchpad.  It's detected and working but advanced functionality like scrolling don't work.  I've tried most of the Synaptics drivers in the repositories but they haven't solved my problem.  I've found a lot of solutions on the forums which call for editing of the Xorg.conf file, but since Hardy doesn't use that any more, has anyone got any advice on how to make scrolling to work?

-Andrew

---

### Post by Rhubarb on 2008-01-15
This is a known bug in Hardy.
[https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/173411](https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/173411)
"it's a well known and deliberate regression for now."

Have a look there, there might be some ways to get it working for you temporarily.

---

### Post by Balk2K on 2008-01-15
Hey, thanks for the link.  I made a temporary Xorg.conf which fixed the problem.  It's great to be able to scroll again!!

-Andrew

---

