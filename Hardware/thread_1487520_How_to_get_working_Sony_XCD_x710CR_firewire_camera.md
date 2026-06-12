---
title: "How to get working Sony XCD x710CR firewire camera"
date: 2010-05-19
forum: Hardware
---

### Post by lev07p on 2010-05-19
Dear Ubuntu Users,

I would appreciate any suggestions on **how to get working a *Sony XCD x710CR* firewire camera** on Ubuntu 10.04.
I am trying to get some frames **with coriander**, in order to know that it is usable under linux. After that I would like to use it with openCV.

**lsmod | grep 1394** gives:
raw1394                22271  0 
video1394              13050  0 
ohci1394               26950  1 video1394
ieee1394               81181  3 raw1394,video1394,ohci1394

**lspci** gives a line with the 1394 controller:
05:01.0 FireWire (IEEE 1394): Texas Instruments TSB43AB23 IEEE-1394a-2000 Controller (PHY/Link)

Coriander gives error message:
"Could not find digital camera on the bus"

What could be the problem? How to get this camera to work?
Any help would be appreciated!


(I am newbie to linux.)

Many Thanks for in advance!
Levente

---

### Post by lev07p on 2010-05-20
bump?

---

### Post by lev07p on 2010-05-23
bump

---

### Post by lev07p on 2010-05-27
bump
Any idea?

---

### Post by dino99 on 2010-05-27
open synaptic and search about "firewire" and "1394":

 install jackd-firewire and the "ffado"* packages, dvgrab (and maybe some more)

google around:

[http://www.ffado.org/](http://www.ffado.org/)

---

### Post by lev07p on 2010-05-29
First of all Thank All of You who have tried to help me!
Maybe other new Linux user (as me) can learn from this, the solution is very simple!! :)
[B]
Solution:

[/B]If you installed Coriander and the appropriate packages as it is pointed, but after running Coriander and it says "Warning: Could not find digital camera on the bus" try to run coriander with superuser privileges!

> sudo coriander

It helped me!

All the best for you,

Levente

---

