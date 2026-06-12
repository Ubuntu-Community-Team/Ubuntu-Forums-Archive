---
title: "Calibrate the pen for Fujitsu Lifebook tablet pc?"
date: 2012-03-05
forum: Hardware
---

### Post by chellrose on 2012-03-05
I just installed Kubuntu 10.10 (with Trinity KDE 3.5) on a Fujitsu Lifebook tablet pc.  Everything seems to work great, but the calibration of the stylus is a bit off.  Is there a way to calibrate it so that the point where I touch the screen will match up with the point that actually gets clicked? :confused:

Thanks.

---

### Post by Favux on 2012-03-05
Hi Sissy13,

You should be able to use xinput_calibrator to get the corrected coordinates.  It's probably in the repositories, maybe as xinput-calibrator.  If that Lifebook uses a Wacom digitizer you would then use a xsetwacom command with the Area parameter and new coordinates to fix the calibration.

---

