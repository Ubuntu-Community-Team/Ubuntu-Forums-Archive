---
title: "800x480 HDMI display using on server."
date: 2014-12-09
forum: Hardware
---

### Post by Raymond Day on 2014-12-09
I got a cheep 800x480 HDMI display to use on my server. Because every now and then I have to move the server box to plug a long HDMI cable it in to a big monitor on the other wall.

This display seems to work good but the text is all most to small to read it.

Is there a way to set the text larger?

All so I like the HDMI display never to go in sleep mode. Is there a way to tell it that?

-Raymond Day

If the display does go in sleep mode. I can't get it back on. Only a reboot get's it to come back on. I can press any key's on the keyboard the display will not wake up.

-Raymond Day

---

### Post by MartyBuntu on 2014-12-09
I hope you find a solution to the problem you're having, but...

...wouldn't it be easier just SSH'ing or VNC'ing into your server?

---

### Post by Raymond Day on 2014-12-09
Yes I can SSH to it. But some times on a reboot it will not boot up and I have to hook up a display on it to see what's wrong. Mostly just have to press Enter.

-Raymond Day

---

### Post by Raymond Day on 2014-12-09
After long last [I found it here.]("http://www.maketecheasier.com/change-console-fonts-in-ubuntu/")

It changed with out rebooting! I did the "dpkg-reconfigure console-setup" and picked VGA then it let me pick 32x16 font size. **It looks a lot better on the LCD screen now!**

Was looking on Google about 3 hours I guess.

Neat got this working good.

The SSH with putty did not change and that's how I wanted it to be. Even after a reboot it worked.

-Raymond Day

---

