---
title: "Fan Noise"
date: 2008-12-05
forum: Hardware
---

### Post by Grubbles on 2008-12-05
After running Ubuntu for about half an hour, I start getting a loud fan noise.  I've been monitoring my fans with lm-sensors and the RPMs don't really increase (20 RPM max)--they actually spin faster in Windows and don't make any noise.  Only three of my fans are connected to the MB, one at both the front and back of the case and the cpu fan.  Originally, I thought it was the fan at the front of my case but I unplugged it and the noise was still there.  The fan at the back of my case is hard to unplug, so I haven't tried that, but it doesn't sound like it's making a lot of noise, and again, it spins faster in Windows.  That leaves me to believe that it must be my cpu fan.  I have one of those fancy Zalman heatsinks and it has a dial to manually adjust the fan speed; I usually have it set fairly low.  What is the possibility that Ubuntu is trying to speed up my cpu fan, but can't because of my manual setting, and that is somehow creating an irritating noise that infuriates me to no end?  Anybody else have any other ideas?  I've tried pwmconfig (I think it's called) and that didn't work.

---

### Post by psusi on 2008-12-05
You will need to look around and see which fan is the one making the noise first, but my guess is that the fans under control are going so slow that the system is getting warmer than it otherwise would, which is causing a fan that is not being controlled by the software to speed up to compensate, which is making noise.

---

### Post by Grubbles on 2008-12-06
Thanks for the speedy reply.

I had the case open a couple of times and it isn't any of the case fans that aren't connected to the motherboard.  I'll pop it open again, probably tomorrow, do some more troubleshooting and hopefully I can find out what's going on in there.

---

