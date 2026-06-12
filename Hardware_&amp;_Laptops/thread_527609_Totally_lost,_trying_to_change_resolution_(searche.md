---
title: "Totally lost, trying to change resolution (searched the forums and Google)"
date: 2007-08-16
forum: Hardware &amp; Laptops
---

### Post by rainwalker on 2007-08-16
I'm in the process of reconfiguring my sister's Inspiron 7500 after a fresh install of Feisty.
The highest resolution I could choose was 1024x768, which didn't really work because Dells apparently have some weird resolution.
I'm aiming for 1450x1024, and I tried adding that into the xorg.conf file but it still wasn't listed as a choice.
I made a little progress following the instructions at [http://aidanloughran.co.uk/wordpress/?p=135](http://aidanloughran.co.uk/wordpress/?p=135)
I used the command ```
sudo dpkg-reconfigure xserver-xorg -phigh
``` and chose "vesa", then selected multiple resolutions that (I'm guessing) were close to what I want;  1440x900, 1400x1050, 1280x1024, and 1280x960. 
I left the original 1024x768 and others, just because I could.
After restarting X (Ctrl+Alt+Backspace), the resolution had changed and looked right from the login screen. But, after logging in, I found that it wasn't quite perfect.
Things are stretched out a bit width-wise, and there seem to be certain horizontal lines of pixels that don't want to behave like the others on the screen. Because of this, sometimes lines and text aren't displayed correctly.
Checking the resolutions window again, I've found that it will only use 1280x1024 (other than the original resolutions). That's about right, but it still isn't correct.

Is there a way to force the resolution I want?

Let me know if I need to post her xorg.conf file.

---

