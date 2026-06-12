---
title: "Ubuntu - AMD A10-5750M -  HD 8650G - Restarts / Crashes"
date: 2014-08-07
forum: Hardware
---

### Post by Steve_Robinson on 2014-08-07
Hi guys!

Ive installed Ubuntu 14.04 to a brand new laptop that had Windows 8 in it.

Its configuration is this:
AMD A-Series A10-5750M (2.50GHz)
8GB Memory (4GB stock Samsung + 4 GB Kingston - DDR3L)
AMD Radeon HD 8650G
[COLOR=#4D4D4D][FONT=helvetica][FONT=Verdana]
[/FONT]Now initially I had installed the proprietary drivers for graphics (fglrx). but then 2D software like Sublime Text performed very poorly. I initially thought it was coz of only 4 GB Ram and so I upgraded to 8 GB (I had to coz I was using 2.8 GB always).
But then someone over on SuperUser told me that I need to go for the Open Source drivers and so I went for it. After that I am facing absolutely no performance issues.

But now the system seems to be restarting occasionally.  Twice a day or so... and today the system just hung and I got red dots all over the place. I was watching a video and the audio seems to be repeating.. and the system was unresponsive. Had to power off and then start it again.

I am a developer and Its very crucial that my laptop does not reboot automatically :) I have checked the logs kern.log, syslog, dmesg and I dont see anything abnormal before the reboot. Just some NetworkManager errors and Ive googled them to find that they are unrelated...
I will attach the logs if you need.

Is this a RAM issue? I am sure I have matched the specs of the stock RAM when I got the additional one. PLease help me out. Thanks![/FONT][/COLOR]

---

### Post by kurt18947 on 2014-08-07
Things I'd try if it were my machine.

- Run memtest for an extended period of time.  That'd test the RAM and if I got a reboot running memtest it seems likely have a hardware problem.

- Did the machine come with Windows pre installed?  Do you get auto-reboot with Windows? Does a non *buntu live session behave any differently?

---

### Post by Steve_Robinson on 2014-08-07
Thanks for the reply Kurt.

1. I'll run memtest today and report how it went
2. I've been running Windows today for nearly 4 hours and it has not rebooted yet. Will work in Windows for 4 more hours.

If it does not happen with Windows, could this be a Ubuntu or AMD Graphics issue? THanks!

---

### Post by mastablasta on 2014-08-07
if it works well with proprietary drivers and not so good with opensource then it's obviously that drivers are to blame here. did you maybe try beta drivers? did you check the AMD site for latest version of drivers? did you check the compatibility for this chip. It seems A4 is good, A6 is so so (good for some problem for others)... could be that A10 is not too good. I would read up a bit on AMD drivers site to see how well the chip is supported. and check the newest drivers and changelogs for those.

manual install is pretty easy. copy and paste a 2 or 3 commands and you are done.

strange though that 2D had poor support in proprietary drivers version. usually it's the 3D that has issues.

edit: are these 2 separate chips? one on CPU and another one? they should both be supported. but oyu may need to configure them? I never had dual GPU.

---

### Post by JDorfler on 2014-08-12
It could be your RAM.  They maybe the same "speed" (ex. DDR3 1600, 1866, etc) but your latency maybe different.  When replacing/adding RAM it's best to have the sticks exactly the same.  If your BIOs/EFi gives you the option of setting the Latency, make sure you set that to exactly what it says on the box.  If your BIOs/EFi can ream XMP 1.2/1.3/etc, then have it automatically use those settings.

---

