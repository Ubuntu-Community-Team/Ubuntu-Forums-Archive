---
title: "dual monitor problem"
date: 2007-05-09
forum: Hardware &amp; Laptops
---

### Post by thysell on 2007-05-09
Hi

I have a nvidia gfx5200 in my laptop wich runs ubuntu 7.04.

I have installed the nvidia driver through automatix and they seem to work.

But, I have two problems. 

1. This is a lesser problem wich really doesn't mean that much to me. It is that when I choose to enable the Desktop effects the borders on all windows dissapear. Meaning, the border where the shutdown-minimize-maximize buttons are. Which is not cool. So, how do I fix that?

2. This is the bigger problem. I have a Samsung LCD-TV. And I want to play my 720p HD-movies on it. But when I plugg it into the laptops VGA-socket and press "detect displays" in the nvidia settings program it doesn't show up. It shows a CRT-monitor with resolution 320x240 instead. The really lame part is that the first time I tried it, it worked. It showed Samsung 1368x768 pixels, it worked fine. I shut it down, went to sleep, woke up, went to work, got home, booted up, thought I was gonna see a movie, but then it showed the CRT monitor instead. I've even tried reinstalling ubuntu with the LIVE-CD without success.

would be grateful for all answer...

regards

---

### Post by raffytaffy on 2007-05-09
ok as to problem 1 i dont really know. i dont use all that fancy desktop effects stuff. However with the second problem. You can input the proper resolution into your xorg.conf by
```
sudo gedit /etc/X11/xorg.conf
``` on the bottom where it says "section screen" in this format "1440x900" '1280x800"  well you get the idea, just use the proper resolution u need. then save it and restart xserver ( ctrl + alt +backspace ) . if the monitor dosent pick up the right resolution from the restart, go change it using the gui tool gnome has into the proper value -> yes it should now be in the choices.

---

### Post by thysell on 2007-05-10
thank you...

I'll try it after work.

---

