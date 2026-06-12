---
title: "Changing from DVI to HDMI out results in huge fonts!"
date: 2012-11-20
forum: Hardware
---

### Post by Cheule on 2012-11-20
Hi there :)

Got a weird problem I've not seen before and can't begin to fathom.

I've recently begun using xfce instead of Unity, on a Geforce GT630. It has two DVI outputs and one HDMI. A long term goal was to switch to HDMI to save huge cable spaghetti at the back of my TV.

Thing is, if I boot up with the DVI output to my TV attached, everything looks normal.

If I boot up connected to HDMI, the fonts and toolbars are massive, despite all the settings saying they are the same!

If I change the fonts down to a more realistic size (and I can't seem to change all of them) then the next time I boot to DVI the fonts are really tiny! :)

I can post screenshots if required, has anyone else had this??

---

### Post by cwsnyder on 2012-11-20
What resolution is listed when you are connected to the HDMI output?

---

### Post by Cheule on 2012-11-20
At the moment, the HDMI doesn't seem to detect the EDID of my Samsung TV, it has a resolution of 1366x768 but 1360x768 isn't listed in Ubuntu, the closest I can get is 1280x720 which is close but not quite :)

---

### Post by cwsnyder on 2012-11-20
If you set your resolution to 1280x720, do you still get huge fonts?

---

### Post by Cheule on 2012-11-21
Yes I do sadly.

The desktop is perfect through DVI but not HDMI.

I am wondering why the fonts and toolbars would care what display technology they are using... :)

---

### Post by cwsnyder on 2012-11-21
I don't think it is the display technology which is being used, it sounds as if the frequencies are fouled up.

Have you tried the basics, that is, make sure the HDMI cables are seated properly, try a different HDMI cable, etc?

---

### Post by cwsnyder on 2012-11-26
Another thing to try is to install **nvidia-current** package and see if that fixes things.

---

### Post by Shuudoushi on 2012-11-26
Also try the latest drivers for your video card and set the res through the software.

---

