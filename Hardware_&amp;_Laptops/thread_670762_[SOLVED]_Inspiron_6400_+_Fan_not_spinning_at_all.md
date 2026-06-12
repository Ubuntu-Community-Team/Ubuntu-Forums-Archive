---
title: "[SOLVED] Inspiron 6400 + Fan not spinning at all?"
date: 2008-01-17
forum: Hardware &amp; Laptops
---

### Post by Chimera76 on 2008-01-17
I'm running Gusty on my laptop for about 3-4 days now...and not once has my CPU fan turned on at all. Its got me a bit worried....so I installed "gkrellm" to monitor the temps (even installed the specific Dell add-on for the fan)...still hasn't turned on.

My worry is because every so often the system locks up for 10-20 seconds at a time. The mouse and keyboard are unresponsive and the screen flickers...all signs of overheating. My fan was purring like a kitten in Windows...cleaned it JUST to be safe with no effect.  

What am I missing?

---

### Post by Z_o-s-o on 2008-01-17
Whats the CPU temp running when these events occur?

---

### Post by Chimera76 on 2008-01-18
+30 degrees...I THINK I have it fixed though....I have it running on low finally...I think it might have just been a setting issue.

---

### Post by Chimera76 on 2008-01-18
No luck....fan is spinning...but my screen is still flickering and shutting down my laptop.... :(

---

### Post by Z_o-s-o on 2008-01-18
I need you to give me temperature readings from the cpu in celcius.

---

### Post by Chimera76 on 2008-01-19
Currently 23 C on battery power

---

### Post by mzembe on 2008-01-19
Maybe this will help:
 > Just to be on the safe side I installed
 i8kutils, gkrellm, and gkrellm-i8k. The fans work and change speeds
anyway but the i8kutils, along with the i8k.ko module, give you control
over the Dell fans and sensors. If you can 'modprobe i8k' in a console
then you have a known working configuration, if it complains and a
'modprobe i8k force=1' inserts the module...
Run 'gkrellm' as the X user, muck around with it to turn off all the
junk and enable the Dell i8k plugin by right clicking the system name
field at the top of the applet .. I get two little propellers with an
'automatic' or 'manual' toggle field and a cpu temp graph - as long as
they seem to be reporting what you hear and you can control them
manually I guess the i8k kernel module works. You can set the temps for
them to cut on and speed up..
If you want to load i8k everytime you just have to add a line to
/etc/modules with 'i8k' - unless force is necessary, then you still add
the line to /etc/modules but you also have to create a file in
/etc/modprobe.d called i8k with a single line 'options i8k force=1'. I
suppose it is a good idea, at least, if you have no trouble inserting
the module. These fans really work fine without the i8k stuff, there is
a related daemon too that might be worth looking into, comes with one of
those packages 'i8kmon'.

Personally, mine seems to work better without the i8k stuff so I'm off to other things.

---

### Post by Chimera76 on 2008-01-19
Mine don't turn at all without it! Thanks for the help, but I got that far myself...i've tried messing around in nvidia-settings and the display menus....and so far *knock on wood* no more issue....I think as I said, it was setting related....it also helped maybe I re-enabled the restricted NVidia driver.

---

### Post by Z_o-s-o on 2008-01-20
The processor won't be overheating at 23C.

- Z_o-s-o

---

### Post by Chimera76 on 2008-01-20
Yes i'm aware of that...I thought I had made it clear that my fan DOES spin right now and its keeping things cool....but i'm still getting the flicker in my screen

---

