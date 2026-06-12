---
title: "bluetooth mouse"
date: 2007-06-07
forum: Hardware &amp; Laptops
---

### Post by ccl4 on 2007-06-07
hello,
i have a logitech v270 bluetooth mouse and want to use it under ubuntu, what should i do?

thanks

---

### Post by steveneddy on 2007-10-18
I have a Logitech V270 bluetooth mouse and it works great here. I installed it tonight under feisty and it was a pain, but after upgrade to Gutsy, it is pure joy.

Gutsy has a better detection capability of bluetooth devices and the overall feel of Gutsy is very good.

Go with the 64 bit version if you can.

:popcorn:

---

### Post by jespdj on 2007-10-18
I'm interested in getting a Bluetooth mouse for my laptop too.

Do you have to install any additional drivers or other software to get it to work in Gutsy, or does it work out of the box?

---

### Post by tonyric on 2007-10-18
It worked out of the box with my v270 and my thinkpad t61

---

### Post by NilsE on 2007-10-18
It should work out of the box but you may worst case have to do the following the first time.

To get address of the mouse: 

sudo hidd --search

That may or may not find it just keep trying and switching the mouse off and on.

To connect:   

sudo hidd --connect 00:03:61:59:32:b1

Change these two lines in /et/default/bluetooth once you get it connected

HIDD_ENABLED=0
HIDD_OPTIONS="--connect 00:03:61:59:32:b1 --server"

Obviously the address in all the above should be changed to the one you detect or the one that is actually on the bottom of your mouse.

---

### Post by steveneddy on 2007-10-19
Yeah - what he said - once it is set up - it stays connected all day at work and I take it home and it works well there, also.

The Logitech V270 is a great mouse - a little small, but it is made for a laptop - comes with a little case, and I bought it at Tiger Direct for $40.

:popcorn:

---

