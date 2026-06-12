---
title: "First Reboot Problems"
date: 2006-02-18
forum: Installation &amp; Upgrades
---

### Post by wisie on 2006-02-18
Hello!

I just installed Ubuntu but when I restart after it has told me to remove the installation disk I seem to freeze on 'xserver-xorg' and this seems to of happened twice??

Is there anything I can do? Can i reboot it again myself and type anything or do I have to re-install?

Cheers

---

### Post by encompass on 2006-02-18
looks like your xserver or graphical side is not set up correctly
try this...
sudo dpkg-reconfigure xserver-xorg and pick your video card... you are unclear just press enter and it will got with the default
what graphics card do you have?

---

### Post by wisie on 2006-02-18
Thanks for the quick reply! I'l give that a go!

I'm not actually quite sure what video card I'm using, it's just something a few years old that I pulled out of an old case, should this matter?

---

### Post by encompass on 2006-02-18
sorry forgot... boot insto recovery mode

---

### Post by encompass on 2006-02-18
and yes it helps... if you want just select vesa device for the card and it may just work for you.

---

### Post by wisie on 2006-02-18
[QUOTE=encompass]and yes it helps... if you want just select vesa device for the card and it may just work for you.[/QUOTE]

Sorry just wanted to ask, how do I boot into recovery mode? :)

---

### Post by encompass on 2006-02-18
if you don't get a console or prompt... you need to reboot... and when it says... booting grub and has a count down... press escape... and a screen with pop up.
from there you select recovery mode.
PM me if you have question... with any of the chat programs.

---

### Post by wisie on 2006-02-18
Thanks to encompass the problem is no more and I'm writing this message on my ubuntu box, thanks so much for your help encompass! Without you I probably would have given up! Very much appreciated! :)

To be honest, I'm not entirely sure what was causing the problem, when i wrote this topic I didn't actually have the box connected to the internet. So I connected it up to the internet and ran 'sudo apt-get install xserver-xorg' and here we are! :) Took a little bit to setup certain packages but all is good now!

Thanks again encompass

---

