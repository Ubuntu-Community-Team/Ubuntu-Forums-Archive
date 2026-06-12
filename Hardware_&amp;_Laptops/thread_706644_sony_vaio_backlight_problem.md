---
title: "sony vaio backlight problem"
date: 2008-02-24
forum: Hardware &amp; Laptops
---

### Post by Ryanmt on 2008-02-24
Im having trouble getting the screen brightness to work on a sony vaio PCG-7D1m. The FN keys refuse to work. Ive ready all the backlight related threads and nothing seems to work. ive tried both sonypi and sony-laptop modules and they dont do anything.

I can change the brightness using the commands

andy@Andys-Vaio:~$ echo 7 > /sys/class/backlight/sony/brightness
 or echo 1. But ajusting it using the gnome applet or plugging the power out etc makes no difference.

Ideally ide want the FN keys working but i mostly need the screen brightness to work. Is there any way to change the command ubuntu runs when you disconnect the power??

Ive installed a deb of fsfn and that makes no difference. Ive manually edited the config file and i cant get anything to happen.. no error messages or nothing. Running fsfn at the terminal just seems to start something.

---

### Post by diegosouza on 2008-03-06
Hi, I have a Sony NR180E and the command xbacklight works! Try it!
Example: xbacklight -set 50 (to turn it 50%)

Good luck!

---

### Post by diegosouza on 2008-03-06
I'm sorry for the last message, now I know what u want. :lolflag:
I'll be trying to do some script helped by "xev" command and compose 2 keys or something with ACPI events.

---

### Post by diegosouza on 2008-03-07
I give up! I can't do that.
Hey Ryanmt, it's better u keep xbacklight for that.

---

