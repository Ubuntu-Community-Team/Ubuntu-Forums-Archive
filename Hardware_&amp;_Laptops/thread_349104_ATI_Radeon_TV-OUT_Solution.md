---
title: "ATI Radeon TV-OUT Solution"
date: 2007-01-29
forum: Hardware &amp; Laptops
---

### Post by Twigg on 2007-01-29
Since I couldn't find anything like this around here for help, I started tinkering with the aticonfig options trying to get my tv-out to work like it does on Windows. This is the series of commands I found that will acomplish this. Basically it makes your desktop twice as wide, with your tv being the second monitor. Useful for dragging over video's and full screening them. Xine is great at this, VLC player full screens it in your other window.

You will need to use the ATI drivers for your video card. There's plenty of tutorials for that part of it though, so just search for 'em.

This will enable the tv-out. Once you enter these commands, hit alt-cntrl-backspace to reset the x server. I'm a Linux novice, so some of these may be redudant, but I have to enter them in this sequence to get mine to work, so i'm assuming everyone else will be the same way.

[PHP]
sudo aticonfig --dtop=horizontal --overlay-on=1 
sudo aticonfig --force-monitor=crt1,tv
sudo aticonfig --tv-format-type=NTSC-M 
sudo aticonfig --force-monitor=tv
[/PHP]

To kill it and make it normal again, use this command. Then do the alt-cntrl-backspace again. You'll want to do this after you've finished watching a movie, because whenever you open a new program with a window up on your monitor, it'll send it over to your tv.
[PHP]
sudo aticonfig --force-monitor=crt1
[/PHP]

---

