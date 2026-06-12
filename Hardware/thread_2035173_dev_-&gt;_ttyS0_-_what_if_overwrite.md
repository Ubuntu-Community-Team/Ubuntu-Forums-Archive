---
title: "/dev -&gt; ttyS0 - what if overwrite"
date: 2012-07-30
forum: Hardware
---

### Post by Shrikee7973 on 2012-07-30
Hello,

I'm working on robotics research with a Pioneer P3AT robot. The robot can be controller through serial port, with an onboard, mounted laptop running ubuntu 10.04. I have a USB to Serial cable, which works fine, but the default mounting is in /dev/ttyUSB0. It would be tedious to make packages work on robot in this situation, because these packages use the port ttyS0 as default. It's in /dev, but I don't know what is it for. I made an experiment: sudo mv ttyUSB0 ttyS0. This way, all the robotics package worked. But I don't know what have I overwritten. Do I lose functionality if I use this method? Otherwise, I would have to change every package's source code and recompile to use ttyUSB0.

---

