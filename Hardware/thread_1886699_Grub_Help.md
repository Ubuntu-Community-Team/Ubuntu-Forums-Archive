---
title: "Grub Help"
date: 2011-11-25
forum: Hardware
---

### Post by jonathon6017 on 2011-11-25
Ubuntu 11.10 works (almost) flawlessly on my machine. 

Most of the problems that aren't working right I can fix (I've just been too lazy to do it yet lol) Due to a virus on the windows side of my laptop I've been forced to use Ubuntu a bit more then normal, which really doesn't bother me. Now as for my issue, whenever I boot up normally I get a blank black screen with a cursor. Nothing else and I am unable to switch to a terminal through CTRL+ALT+F(x) 

Now if I edit the grub configuration at bootup and change gfxpayload (I believe I got that right it's gfx something :) ) to "text" then Ubuntu boots up fine with normal graphics. I was wondering what text files can I configure so that that change will be permanent rather then me changing it every time I boot

---

### Post by dabl on 2011-11-25
/etc/default/grub

---

