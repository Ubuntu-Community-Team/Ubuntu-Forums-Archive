---
title: "Touch screen problem with HP TouchSmart tm2"
date: 2010-11-17
forum: Hardware
---

### Post by lotech on 2010-11-17
Installed Maverick on a HP TouchSmart tm2, most things worked except the screen, firstly the screen will reset to the dimmest on boot up, I must manually turn up the brightness, secondly the cursor will jump crazy when I turn the screen so that it is in the tablet setting, I must slightly 'unfold' the screen to stop that, thirdly when I rotate the screen 90 degree with the display setting, the cursor will be serious out of position with touch input.

I know the standard OS may not fully support tablet, I just wondering if there is a package or something I can install to fix the screen, I also want handwriting support...

---

### Post by Favux on 2010-11-17
Hi lotech,

I think we need to figure out what driver has your Wacom digitizer.  It doesn't sound like the Wacom driver.  Enter in a terminal:
```
xinput --list
```
and
```
dmesg | grep [Ww]acom
```
and
```
lsmod | grep wacom
```
and post the outputs.

Then we can deal with rotation.  Magick Rotation should work for you.  It's linked on the [Rotation HOW TO]("http://ubuntuforums.org/showpost.php?p=6274392&postcount=1").

---

