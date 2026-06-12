---
title: "how to configure 2 monitors with nvidia in ubuntu 12.04"
date: 2012-05-18
forum: Hardware
---

### Post by Salvagluque on 2012-05-18
Hey guys,

I have 2 monitors and it turns out that ubuntu 12.04 doesn detect them but nvidia does, so I get a big  white screen on the right in which the cursor turns into a black X. I noticed that displys doesn't detect a second screen nor let me enlarge the screen size. In the nvidia  x server settings I can see the second monitor but nothing happens. I have installed ubuntu 12.04 just yesterday. Thanks guys.

I already installed the nvidia driver following these instructionshttp://www.unixmen.com/201205-nvidea-295-49-has-been-released/

---

### Post by Salvagluque on 2012-05-18
it seemed to be solved some how. What I did? Just kept turning on and off option in the displays and the nvidia x server settings. The displays keep saying I cannot apply a 3360x1050 (which I&#7743; currently at) and the nvidia settings I could somehow land them in twinview at 1680x1050 with no "twinning" at all. I ended up with the two screens-wide desktop but with everything dening it. Also I kept the drivers for nvidia in the current version, the one that is recommended.

So seriously I have no idea why this happened.

Then I restarted and everything went to nag me about how and why ]ubuntu can't do 2screens wide (somehow openning in xfce mode). Act followed, I logged out and re-entered in ubuntu mode. Then I put the settings like before twinview, etc. And also savedd to the x configuration. Logged out and logged back in. And, seemingly, it's working fine in a 2 screen-wide desktop, in twinview mode (with no replication in the 2nd screen). 

So, WEEEIRD. I'm totally mistified by this, but the heck, it works.

see ya, dudes.

---

### Post by abisdad on 2012-06-02
Tried that lots, didn't work for me...

This is related to this:

[http://ubuntuforums.org/showthread.php?p=11650060#poststop]("http://ubuntuforums.org/showthread.php?p=11650060#poststop")

Rob.

---

