---
title: "Plotter problem"
date: 2011-10-29
forum: Hardware
---

### Post by tolletrolden on 2011-10-29
Hi - when i use "cat hpgl-file > /dev/ttyACM0" anything works fine as long as its a simple drawing.

When more complex drawing is sent - the plotter hangs.

If i copy same plotter file to sd card and put it in plotter - the file is plotted as it should.

That leaves me with an usb transmission problem - i think.

Any suggestion to solve this problem?

---

### Post by tolletrolden on 2011-11-15
A little update.

In a terminal i can write ttylog -b 38400 -d /dev/ttyS0 > log.txt

Then plotter is working as it should - no problems at all.

If i hit ctrl z to stop the ttylog - than plotter stops working - tryed this severel times.

That i think is a strange error:confused:

---

