---
title: "stuck at 800 600 nvidia"
date: 2010-04-30
forum: Hardware
---

### Post by deymer on 2010-04-30
i just tried to fix my friends computer by installing linux. unfortunately, i'm stuck at 800x600 resolution, and can't get any higher. can anyone help me with this? it has an nvidia graphics card, sorry i don't have any more specs to go with that.

-deymer

---

### Post by partymetroid on 2010-04-30
Which version of Ubuntu are you using?  What type of screen is your friend using?  (e.g. CRT, LCD)

And if you can, can you tell us what graphics card your friend has?

Even without that information, typing this into the console might resolve the issue:

```
dpkg-reconfigure -phigh xserver-xorg
```Then reboot. :KS

Not sure if this is a solution, but it won't at all hurt your installation. :popcorn:

---

### Post by deymer on 2010-04-30
i typed in the command you gave me, and restarted the machine. it still only gives me 800x600 resolution.

is there a command i can put into console to see what type of graphics card i am using? all i know as of right now is that it was made by nvidia. the monitor is a flat screen, im' not sure if it's lcd or not.

---

### Post by empian on 2010-05-01
I'm having a similar problem with 10.04. I can't increase my resolution above 1024 x 768. It was set at 1280 x 960 before I upgraded. Frustrating :-/

---

