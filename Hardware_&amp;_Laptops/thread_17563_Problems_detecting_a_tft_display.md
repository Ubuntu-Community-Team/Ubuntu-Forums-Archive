---
title: "Problems detecting a tft display"
date: 2005-03-01
forum: Hardware &amp; Laptops
---

### Post by klaym on 2005-03-01
Hello!
I bought myself an Acer TFT display (AL1714: 17", 14ms with speakers, 249e. here in Finland a bargain!)

I then got rid of my old crt monitor and plugged the new tft on. But when I tried to run Warty, after the initial load-ups and just before the splash screen I get a "Input not support" - box floating around. I guess I should reinstall ubuntu so it could properly detect my new monitor, but is there any other way to make ubuntu recognize it? If there isn't, is there some way to backup all my contemporary settings? (such as gnome theme, xchat settings, firefox plugins, and of course everything in homefolder). Thanks!

---

### Post by cuoog on 2005-03-01
It's hard to say what the issue is, can you tell us a bit more about your config; i.e. did it work before with the CRT, what video card do you have, what driver are you using, warty or hoary, etc...

I have a very similar monitor (Acer AL1715b) so I can tell you it works.  There is no reason that any monitor shouldnt work.  I will tell you that I couldnt get Ubuntu to load at all (same error you are having) until I booted to a prompt and installed the nvidia binary driver.  For me, NV never worked.  After that it worked like a charm.

At the minimum, when you add the new monitor youll probably have to reconfigure Xfree86 (if you are on warty) in order to run at the proper resolution.  However, the monitor should work even at the lower resolution, just be pixelated and have poor response.

---

### Post by hashimoto on 2005-03-02
Your problem probably lies in the incorrect horizontal and vertical refresh rates which are different in your new TFT.
Have your monitor specs available and boot to safe mode. You will end up in text mode. Log in and then run:
sudo dpkg-reconfigure xserver-xfree86
Answer all the questions (they are not that difficult) and give correct values to those that have changed (refresh rates & resolution).

---

### Post by klaym on 2005-03-05
Thank you cuoog and hashimoto, it now works like charm! Changing the horizontal and vertical refresh rates did it.

---

### Post by hashimoto on 2005-03-05
I'm glad we could be of help!

---

