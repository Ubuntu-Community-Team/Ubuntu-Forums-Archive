---
title: "IBM Thinkpad T30 - keyboard issue"
date: 2007-09-12
forum: Hardware &amp; Laptops
---

### Post by Garyu on 2007-09-12
I managed to completely mess up my keyboard configuration on my IBM Thinkpad T30.

Everything was working fine after installation. Then I was trying to get my ATI graphics working with 3D, so I used the "sudo dpkg-reconfigure -Phigh xserver-xorg" to only mess about with my graphics. For some reason, my keyboard was then changed from "sv" (swedish) to "us" in the /etc/X11/xorg.conf 

So I manually edited with "gksudo gedit /etc/X11/xorg.conf" and changed "us" to "sv" in the keyboard settings. Then when I rebooted Gnome gave an error report saying something about keyboard mismatch between gnome and X server. I just clicked OK on that one.

Everything seemed to work at first, I have all my swedish characters in the right place and so on. But now I discovered that I can't write backslash. Very annoying. So I looked around in the System menu for Settings and Keyboard. There it says I have a 105-key standard keyboard, which is obviously wrong. So there are two keyboard entries with Thinkpad, but none of them match. I counted and think I got it to 88 keys or so (depending on whether or not I should count the volume buttons and such). Also, when I tried to change to the Thinkpad entries in the gnome keyboard settings (even though the name did not match with my T30) I got the same Gnome error mismatch with X server. 

So, how do I get back my original keyboard setup so I can use the backslash key and others as normal?

---

