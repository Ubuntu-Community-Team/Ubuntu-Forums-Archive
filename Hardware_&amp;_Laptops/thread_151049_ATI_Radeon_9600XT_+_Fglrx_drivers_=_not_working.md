---
title: "ATI Radeon 9600XT + Fglrx drivers = not working"
date: 2006-03-27
forum: Hardware &amp; Laptops
---

### Post by so0le on 2006-03-27
Okay, so, here's what I did:

I installed fglrx drivers like [this]("http://https://wiki.ubuntu.com/BinaryDriverHowto/ATI") guide tells. I boot the computer, and do 'fglrxinfo', it only gives this to me:

display: :0.0  screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.2.1)

I have just installed my Ubuntu, and this is 5.10 32-bit Breezy.
uname -r command gives: 2.6.12-10-686
When I run glxgears, the test runs very slow.
Cedega system tests fail the first two sections, which are OpenGL and 3D Accerlation.

Please help me, I really want my Quake 2 working. :l

My specs are:

AMD Athlon 2800+ 64
Asus K8S-MX Motherboard
SiS integrated soundcard
Realtek network card
Sapphire ATI Radeon 9600XT

---

### Post by japs_it88 on 2006-03-27
shouldn't you have a 64-bit installed?

anyhow, try to run sudo fglrxconfig and follow all the steps, it worked for me.

---

### Post by so0le on 2006-03-27
No, some programs do not support 64-bit. I have ran that config once, it just gave me the same results after that. Expect that I configed my mouse wrong from there.

---

### Post by RoboJ1M on 2006-03-27
search these forums for fglrx.
There is a big HOWTO on how to remove the breezy packaged version of fglrx and install the latest version from ATI.

Mine worked with both for 3D, but neither with 2D though :(

The latest version has a desktop app to configure TV out and stuff, it's much nicer that your usual xorg.conf-in-a-text-editor gumf.

J1M.

---

### Post by so0le on 2006-03-27
I have tried that one too, 3 times, didn't work. Always those Mesa drivers.. I hate those 3 lines so much.. In BIOS I have set up AGP/Int-VGA, 8x and no fastwrite.

---

