---
title: "ThinkPad T60 Fan Problem"
date: 2008-09-07
forum: Hardware
---

### Post by chaosrl on 2008-09-07
Hey everyone! In the past few weeks, I've noticed that my CPU fan makes a CRAZY loud whirring noise when I'm booted in Ubuntu. I dual boot Hardy Heron and Vista, and when I'm booted up in Vista, the sound doesn't occur. My thoughts:
Ubuntu perhaps makes my fan spin up at a lower temperature than Vista, or makes it spin faster, hence the sound. It only occurs at high RPMs. I've taken the whole thing out and thoroughly dusted my computer and the sound persists.

My question is: is there any way to make sure 100% that it is a hardware problem? Stress testing in Vista or something? Also, is there a way to control the fan in Ubuntu so it doesn't spin up so fast/quickly?

If these don't work, I'm considering buying a new fan assembly, as this noise is unacceptable in class/the library for a college student. Thanks!

Jeff

---

### Post by jett on 2008-10-15
the fan problem is a T60 problem. Do a search on "T60 fan noise" and you'll see several other threads discussing this.

I am guessing that in Vista it is setup to run not at "balanced" (as opposed to power-saving, or performance) hence the CPU runs lower than its rated speed thereby not producing as much heat. I am not sure if such "speed stepping" also occurs in Ubuntu.

My T60 is in a much worse state than yours. The fan noise happens even in Vista. It doesn't seem to be temperature related because GPU is temp is at 62, CPU at 54 yet the fan is still at 3000 RPM.

---

### Post by jett on 2008-10-16
Just found the link to [_TPFanControl for Linux_]("http://www.thinkwiki.org/wiki/How_to_control_fan_speed"). It also contains other useful info.

Here's a [_link_]("http://www.staff.uni-marburg.de/~schmitzr/donate.html") to the version for Windows in case you need it.

---

