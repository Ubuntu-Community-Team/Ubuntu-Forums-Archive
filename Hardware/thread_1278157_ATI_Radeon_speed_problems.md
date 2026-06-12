---
title: "ATI Radeon speed problems"
date: 2009-09-29
forum: Hardware
---

### Post by barna on 2009-09-29
Hi
I have a Toshiba Satellite, with the following graphics card:
ATI Technologies Inc Radeon Mobility 7000 IGP
With Ubuntu 7.10 the closed-source fglrx driver was used, and gave perfect performance. However, this driver (provided by ATI) is not supporting anymore these old graphics cards, and an open-source driver, xserver-xorg-video-radeon is used now. In Ubuntu 9.04 this driver was lacking some features, and the 2D display of a cad software (VariCAD) was unusable. The driver shipped with Ubuntu 9.10-alpha seems to be providing those lacking features, the CAD software is running, but with terribly slow performance, so it is practically unusable again... 
Are there any tips to make the performance quicker? Or can one expect that the open-source driver improves, giving better performance? If not, I will need to stick to ubuntu-7.10 until my notebook dies and I buy a new one.
Thanks
Daniel

---

### Post by barna on 2009-09-30
This is my Xorg.0.log, maybe somebody understands more about it than I do:
[http://barna.web.cern.ch/barna/Xorg.0.log](http://barna.web.cern.ch/barna/Xorg.0.log)

---

### Post by benmoran on 2009-09-30
The open source drivers are improving by leaps and bounds every month. It's amazing how fast they have caught up. Currently only OpenGL 1.5 is supported, but that should be enough for your program. 

To get the latest drivers, try running the Xorg Edgers PPA (google search). Also, you can read up about graphics stuff over at Phoronix.com

---

### Post by barna on 2009-09-30
Hi,
Thanks a lot, it's nice to know that they are steadily improving. I feared that these speed problems are due to features of the graphics card, which the closed-source proprietary driver could use, but the open-source can not. 
It seems that there are currently no newer versions of this driver than the one in ubuntu 9.10, so I wait for future releases.

Some further diagnostics: if I drag the 2D drawing in this cad application slowly over a long distance (i.e. the graphics is redrawn many times), there is a many-second lag between the mouse movement and the graphics movement, and Xorg is taking 100% of my CPU.
If I drag the drawing very quickly and then release the mouse button, the drawing is not redrawn many times, only at the final position, and the reaction is therefore acceptable.

Thanks

---

