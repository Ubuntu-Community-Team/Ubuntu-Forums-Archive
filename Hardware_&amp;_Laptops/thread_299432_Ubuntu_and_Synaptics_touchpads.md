---
title: "Ubuntu and Synaptics touchpads"
date: 2006-11-14
forum: Hardware &amp; Laptops
---

### Post by mykrob on 2006-11-14
Hi-
I have tried Ubuntu several times, and always ended up going back to my favorite Mepis.
One of the biggest issues I had with Ubuntu was on my laptop, a Compaq V5204NR. THe touchpad works a bit, but is very jumpy, meaning i can keep my finger in one place, but the cursor will jump ot another area on screen and jiggle.. In Mepis, i have a GUI to setup my touchpad

[[IMG]http://img218.imageshack.us/img218/9782/desktop2ek8.th.jpg[/IMG]](http://img218.imageshack.us/my.php?image=desktop2ek8.jpg)

dont know what it does, but it makes my touchpad work correctly in Mepis and enables my scrolling zones on the touchpad too..

I assume it edits the xorg.conf file somehow.. What can I do to get my pad working right in Ubuntu? I'm really interested in UbuntuStudio, but the touchpad not working is a real problem.. This is my main hurdle.. I got the wifi working fine.. i even have good Intel High Def Audio, thanks to Tobin Davis's alsa driver hack. (can document this if anyone needs it)

thanks,
-myk

---

### Post by ThrobbingBrain66 on 2006-11-14
try installing gsynaptics
```
sudo aptitude install gsynaptics
```
its a GUI and will allow you to configure your touchpad

---

