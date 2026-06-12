---
title: "Thinkpad T400 &quot;disengaged&quot; fan speed slower than on windows"
date: 2015-10-21
forum: Hardware
---

### Post by simon118 on 2015-10-21
When setting the speed to "disengaged" via thinkfan, I only get up to around 3.5k RPM on Ubuntu 14.04. That is almost 1.5k less than on Windows 7 with TPFanControl, so I wondered if there is a way to tweak it. I am currently doing some CPU intensive stuff and am running into heat problems. Any ideas?

---

### Post by tgalati4 on 2015-10-21
Some reading:  [http://zmalltalker.com/zlog/thinkfan.html](http://zmalltalker.com/zlog/thinkfan.html)
[http://overtag.dk/wordpress/2012/03/to-all-my-thinkpad-friends-running-linux/](http://overtag.dk/wordpress/2012/03/to-all-my-thinkpad-friends-running-linux/)

Perhaps a BIOS/firmware update will fix the problem.  Does speed 7 and disengaged give you the same, maximum speed?

Understand that it may take a few seconds for the fan control to disengage, so set your fan speeds more aggressive.

---

### Post by simon118 on 2015-10-22
Hm, ok maybe it is the BIOS. Speed 7 and disengaged are both around 3.5k, and it does not speed up anymore even if I am waiting. Thanks!

---

### Post by simon118 on 2015-10-31
It seems I already have the newest BIOS version installed. Any other suggestions? I wanted to try out some neural network tools, but running both CPUs at 100% on Linux lets the temperatures jump up to 90°C and probably more.

---

### Post by tgalati4 on 2015-10-31
Pull the heatsinks, use Arctic Silver or a decent ceramic heat paste, apply the proper amount (watch a youtube video on how to 9o it).  Blow the fan and vents with an air compressor, lubricate the fan bearing.  Assemble and test.  If you are still getting heat problems send an email to Lenovo about the issue.

Turn on dynamic clocks for your GPU.  What hot does your GPU get during these sessions?

Otherwise, run Windows to do your number-crunching.

---

