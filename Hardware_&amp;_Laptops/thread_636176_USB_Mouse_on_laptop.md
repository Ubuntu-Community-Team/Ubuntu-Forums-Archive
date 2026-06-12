---
title: "USB Mouse on laptop"
date: 2007-12-09
forum: Hardware &amp; Laptops
---

### Post by xodeus on 2007-12-09
Hi, I would like to fast switch between my USB mouse and the touchpad on my Laptop.
So when I'm using the laptop without the USB mouse, it should be with the touchpad, but when I stick my USB mouse into the laptop, it should detect the mouse and I should be able to use it right away. Is this possible?

---

### Post by rodo-&gt;dave on 2007-12-09
Hi. I did something similar by following the directions on this thread:
[http://ubuntuforums.org/showthread.php?t=271052&highlight=disable+mousepad](http://ubuntuforums.org/showthread.php?t=271052&highlight=disable+mousepad)

I turned my mousepad off in Sessions "synclient touchpadoff=1"
I mapped a gnome-terminal to CTRL+ALT+T on Keyboard shortcuts (this way I can start the terminal and run the command to enable the mousepad).
and wrote a shell script to run "synclient touchpadoff=0" 

Hope this helps.

---

