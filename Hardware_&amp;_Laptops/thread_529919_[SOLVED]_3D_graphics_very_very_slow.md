---
title: "[SOLVED] 3D graphics very very slow"
date: 2007-08-19
forum: Hardware &amp; Laptops
---

### Post by bravemenrun333 on 2007-08-19
I have a Lenovo R60 Thinkpad witha X1400 graphics card.

I tried running FlightGear, a game which runs just perfect under windows. But under ubuntu, it is very very slow. How can this be?

---

### Post by w4ett on 2007-08-19
Have you installed the restricted driver fglrx for your graphics chipset or are you using the open source xorg driver ati?   The open source driver, while providing a some 3d rendering, is not really game capable.  Here is a how-to for the driver installation:

[http://ubuntuforums.org/showthread.php?t=414194](http://ubuntuforums.org/showthread.php?t=414194)

---

### Post by EXCiD3 on 2007-08-20
Once you install the drivers, open a terminal and type "glxgears" and then post several of the average fps that it displays. That should tell us how well your driver is working.

---

### Post by bravemenrun333 on 2007-08-20
I have now installed the driver following the descrition.
The average FPS in glxgears is ~156 FPS when focused to the application window and ~1220 FPS when having the window in the background.

is this ok?

EDIT: When I open the restricted driver manager tool it says that the driver is enabled but the box is not checked! Do I have to check the box to fully enable the driver?

---

### Post by bravemenrun333 on 2007-08-20
can someone help me?

---

### Post by w4ett on 2007-08-20
check the box in the restricted drivers and then reboot.  This will enable the new video driver

---

### Post by bravemenrun333 on 2007-08-20
I am using now Driconf, with all options enabled, my new FPS in glxgears is average 2900 FPS!

I am going to check how FlighGear works now and then report back.

---

### Post by w4ett on 2007-08-20
Super....looks like you got it.

---

### Post by bravemenrun333 on 2007-08-20
yeah thanks a lot, I have now FPS of 35 in FlightGear, but heavy sound stutters. Dont know why..

---

### Post by w4ett on 2007-08-20
Maybe a problem with alsa??   IMO...Please mark this thread as "solved" and start a new thread for the sound issue.

---

