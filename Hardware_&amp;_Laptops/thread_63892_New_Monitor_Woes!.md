---
title: "New Monitor Woes!"
date: 2005-09-09
forum: Hardware &amp; Laptops
---

### Post by RossC0 on 2005-09-09
Hi,

I've changed my monitor to a LG Flatron L1715S, ran :

sudo dpkg-reconfigure xserver-xorg

To set the resolutions - so I can see the screen! However now my icons are black and the screen color depth / definition is off.   Everything seems to be very white.

Any pointers on what I need to do to fix this ?

---

### Post by RossC0 on 2005-09-12
I think it must be a bug somewhere - as I have tried the flatscreen on another Ubuntu system and have no problems - the white levels are correct.

I'm now using my old monitor until I can find a solution!  I tried manually changing the gamma settings - but no joy.

The only thing different between the systems is the graphics card - but I cant see why it would be fine on an old monitor but be too light on the new lcd monitor on the one system.

Any ideas / advice ?

---

### Post by tseliot on 2005-09-12
1) Which graphic card is yours?

2) Can you post your /etc/X11/xorg.conf ?

3) do you know the horizontal and vertical refresh rate of the monitor (try the manual or in google)

---

