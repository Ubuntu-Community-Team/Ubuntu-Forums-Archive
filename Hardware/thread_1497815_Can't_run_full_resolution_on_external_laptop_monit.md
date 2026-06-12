---
title: "Can't run full resolution on external laptop monitor"
date: 2010-05-31
forum: Hardware
---

### Post by picarune on 2010-05-31
Hi Folks,

I just set up my trusty old T60 to dual boot Lucid, and I would like to set up an  external Samsung 2253 LCD. X doesn't recognize the external monitor, and therefore won't run it at full resolution.  I have found from poking around the forums that I must generate a new Xorg.conf file, and I'm wondering if I need to call out the laptop LCD as well as the external in the screen section, and if I am going to break X if I don't.

I just did this on my desktop box which is running an Nvidia 7300LE, and fixed the same problem by calling out the refresh rates so X knew what it was working with.  Also wondering if  I can do this automatically by hooking up the external monitor and running dpkg - reconfigure xserver-xorg or something similar.

Thanks!

---

### Post by dino99 on 2010-05-31
often old xorg.conf break with lucid as kernel now deal X, so rename yours. If you want to recreate and tweak one, use X -configure or nvidia-settings (other methods are deprecated)

you need these packages installed: nvidia-current, nvidia-current-modaliases, nvidia-common, nvidia-settings

nvidia-settings could be able to set your config. If it fail: take note of the info about your hardware to tweak your xorg.conf

---

### Post by picarune on 2010-05-31
Hi Dino

I have the box with the nvidia card running OK.  The issue is with  a Thinkpad with an Intel 945 adapter.  I guess my question is how much info I need to add, both monitors or just the external, and where the file goes.

Thanks!

---

