---
title: "Problems with sound and resolution"
date: 2007-10-12
forum: Hardware &amp; Laptops
---

### Post by King-Raven on 2007-10-12
Hello,

I made my first tries with Ubuntu.
I installed version 7.04 and it looks nice.

But I have 2 problems:
[LIST]
[*]I have a Elitegroup K7S5A Motherboard with integrated soundcard and don't have any sound...
[*]I have a nvidia Geforce 6200 graphic card and a Sony SDM X82 TFT monitor.
The monitor needs resolution 1280*1024 but I can only select 1024*768 or lower...
[/LIST]

What can I dou ?
Would be nice if you could help me...

Thx in advance.

Btw... I am only familiar with Windows ;)

---

### Post by cubeist on 2007-10-12
I can't help you with your sound, but for the graphics are you using the restricted driver (System/Administration/Restricted Driver Manager)?  If you aren't, try enabling that and see if you get better resolution.

If you are using the restricted driver type "nvidia-settings" into the terminal and that will launch a program that will let you select the correct resolution.

---

### Post by King-Raven on 2007-10-14
Hello cubeist,

Thx. That helped for the resolution topic ;)

But there is still the sound problem...
any ideas ?

King-Raven

---

### Post by infra_red_dude on 2007-10-14
I think this mobo uses SiS7018 Audio chipset. You may wanna search for drivers for this particular chipset.

---

