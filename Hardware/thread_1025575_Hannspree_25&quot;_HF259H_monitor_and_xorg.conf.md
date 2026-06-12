---
title: "Hannspree 25&quot; HF259H monitor and xorg.conf"
date: 2008-12-30
forum: Hardware
---

### Post by Murwiz on 2008-12-30
I have a brand-new monitor from Hannspree, but I cannot get a display resolution above 1024, and widescreen modes are completely absent. Is there a known-good xorg.conf setup for this? I have tried nvidia-settings, envy, and dpkg-reconfigure -phigh xserver-xorg, all to no avail.

---

### Post by Murwiz on 2008-12-30
I don't know if this makes a difference, but the graphics card is a Quadro NVS 280, 64MB. I'm starting to worry that it may not be able to handle widescreen.

---

### Post by pietjanjaap on 2008-12-30
gksu displayconfig-gtk
Here you can see if your monitor is recognized.
And you can try to change it.

Today i got a lot of problems wenn installing driver for my videocard.
With envy remove everything,(reboot)
Then go to recovery mode, xfix
then go to textmode,
Start envy in textmode Type: sudo envyng -t
Then you get a menu, install driver.
reboot

Then everything was ok

---

### Post by Murwiz on 2008-12-31
The answer here *seems* to be the graphics card, and not the monitor: I'm using the graphics card's DVI output (there's no VGA output), and the card only supports widescreen for analog/VGA. I'm going to get an adapter and try again.

Meanwhile, I have to say I'm underwhelmed with the Hannspree for one big reason: the display as I have it now shows a very distinct color shift from top to bottom. E.g., a solid-color window will be much lighter at the bottom (and text much harder to read due to differing contrasts). I may end up returning this if I can't figure out how to correct it.

---

