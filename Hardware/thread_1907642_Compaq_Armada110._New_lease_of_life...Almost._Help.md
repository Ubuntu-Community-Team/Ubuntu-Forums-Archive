---
title: "Compaq Armada110. New lease of life...Almost. Help!"
date: 2012-01-11
forum: Hardware
---

### Post by Fenris_rising on 2012-01-11
Hello all

I have been attempting to get a compaq Armada 110 laptop going again.

It had had windows XP installed, by ne, a year ago for my wifes step dad. Up till now it had been working OK but a reinstall hasn't helped and having checked out a few areas it seems the small HDD is just being packed solid with so much bloat it just can't cope.

So I turn to my trusty Ubuntu/Linux OS. I have been windows free for four years now :)

Xubuntu was chosen with and Xfce front. The install went as well as a linux install does but on booting I get the xubuntu splash screen then the screen goes blank.

With a little bit of 'play' I managed to boot into recovery mode and using the 'run low graphics' option had a desktop up and running. Most pleasing was the fact that the belkin wireless adapter that was plugged in to the lap top was working straight off the bat.

I have tried a couple of fixes to the xorg.conf, As seen on this forum, but unless I boot up into recovery mode I just end up with the blank screen.

Has anyone got a definitive idea of how to have the laptop boot up properly?

The GPU is -

Graphics Controller- 	Trident CyberBlade i7 Shared Video Memory (UMA)

Mechanically the laptop seems very robust and does work well, and faster than windows, barring this slight issue.

regards

Fenris

---

### Post by Buntumatic on 2012-01-11
Does Xorg trident driver load? Clues should be in Xorg log.

---

### Post by mastablasta on 2012-01-12
also have you tried various boot parameters? for example nomodeset ?

---

### Post by Fenris_rising on 2012-01-12
Hello Chaps.

The trident xorg driver is installed according to synaptic. So far non of the boot parameters have helped get beyond the black screen.

Having looked at the logs it seems the trident driver is being loaded, the screen size 1024x768 is identified correctly, but then there is line after line of =

(II)TRIDENT(0):Not using default mode **"A screen size"** (vrefresh out of range

Also many similar lines with various screen sizes with hrefresh out of range.

The ranges it seems to try are -

hsync range of 28.00-38.00kHz
vsync range of 43.00-72.00 Hz

Now I think I have looked at a log that is of a vesa boot up. This must be the low res option I am using to get a GUI.

This has settings of -

hsync 31.50-47.30kHz
vsync 56.00-59.87Hz

Would this be a hint of a cure?

Irritatingly I have seen other people hailing either xubuntu or crunchbang as having breathed new life into the same laptop but seemingly without issue. Or at least they haven't mentioned any.

I now have the splash screen but nothing beyond this. At least the screen is staying on now :D

regards

Fenris

---

