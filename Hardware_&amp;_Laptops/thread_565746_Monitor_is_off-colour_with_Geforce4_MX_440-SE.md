---
title: "Monitor is off-colour with Geforce4 MX 440-SE"
date: 2007-10-02
forum: Hardware &amp; Laptops
---

### Post by kasio on 2007-10-02
Hi,

I have a Nvidia Riva TNT2 32MB and I got an old Geforce4 MX 440-SE 64MB that I am going to upgrade to.

Using my current monitor with the Riva, everything is fine, however, when I put in The Geforce4, The colour goes off, and oranges become green, greens disappear etc.

This is from boot and I have tried another monitor but to no avail. They are both old CRT models. I tried using xgamma and nvidia-settings and the monitor controls to try and fix it but it didn't work.

I was wondering whether I might need to upgrade to a flat screen to get the Geforce4 to work.

Thanks,

Kasio

---

### Post by Curtiss on 2007-10-03
Did you disable the graphics controller in the BIOS first for the on board Nvidia Riva TNT2 first before instaling the Geforce2 MX 440-SE. Sounds like both graphics controllers are dukeing it out with each other. Thats the only thing I can think of.

Curtiss

---

### Post by kasio on 2007-10-03
The Riva was an AGP card and I replaced it with the Geforce4.

---

### Post by kasio on 2007-10-03
Maybe upgrade to LCD/TFT?

---

### Post by Soybean on 2007-10-03
You mentioned that the GeForce4 is also old... is it used? There could be something wrong with it. Bad colours like that would normally make me think 'bad cable,' but since you're only getting it on one video card and not the other, my next guess would be a problem with the connector on the card. 

It might also be a problem with the drivers, maybe... it's not super likely, I just mention it because it's fixable, which makes it a nicer theory. Are you still using the same drivers you were with the Riva? Maybe try switching to just generic vesa drivers -- if that fixes the colours, then you'll know it's a driver thing and you can try to find proper drivers.

The problem isn't with your monitor, since it works fine with the other card... so switching to an LCD won't help.

---

### Post by kasio on 2007-10-03
Ubuntu automatically switched to the right driver (nvidia-glx). But I'll try your suggestion. The card is used, so i'll try cleaning the connector.

Thanks!

---

### Post by kasio on 2007-10-03
I cleaned the connector, but as msson as the computer turns on, the colour is off. Also the red gamma controls in xgamma don't work...

---

### Post by Soybean on 2007-10-03
Well... it sounds to me like your Geforce4 is broken. :( But I'd recommend getting a second opinion. Do you have another computer you could test it in? Or if you happen to know someone who's good with a soldering iron, maybe you could get them to take a look at it. It might be a solderable problem.

---

### Post by kasio on 2007-10-04
I have a computer with similar specs. I'll try that.

---

