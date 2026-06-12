---
title: "One remained problem a start/shutdown with ATI Radeon Mobility M6 LY"
date: 2010-06-12
forum: Hardware
---

### Post by rbhausoul on 2010-06-12
[FONT=Arial][COLOR=Black][B]Since some time I use Ubuntu 10.04 on a Compaq Laptop Evo N600c. In the beginning it was hard to configure the graphics of the ATI Radeon Mobility M6 LY, but with this form it worked: [http://ubuntuforums.org/showthread.php?t=912034&highlight=ATI+Radeon+Mobility+M6+LY+dri%2C+Progress%3F%3F]("http://ubuntuforums.org/showthread.php?t=912034&highlight=ATI+Radeon+Mobility+M6+LY+dri%2C+Progress%3F%3F")

Now I have one little problem left: when I startup Ubuntu my screen goes black with a terrible color-deformed box. After the desktop is loaded everything looks fine. But when I Shutdown Ubuntu a graphical error appears again: the whole screen is a deformed mix. For me it looks like the screen-resolution is false in both modes.

Does anyone know how it can be fixed?[/B][/COLOR][/FONT]

---

### Post by quixote on 2010-06-23
Not sure if this relates to the problem, but apparently there's a [hardware bug]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/565607") in the M6 LY.

On the [X quirks page]("https://wiki.ubuntu.com/X/Quirks") in the Ubuntu wiki, they list some workarounds.  One of them is to install the fglrx driver, which is easy in synaptic.  Is that the driver you're using?  If not, install it and see if it helps.  If it doesn't, that X Quirks page also has an xorg.conf edit which sounds worth trying.  Just come back with further questions, if and when they come up.

---

