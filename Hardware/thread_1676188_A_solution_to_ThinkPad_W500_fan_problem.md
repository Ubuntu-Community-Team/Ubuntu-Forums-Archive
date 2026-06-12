---
title: "A solution to ThinkPad W500 fan problem?"
date: 2011-01-26
forum: Hardware
---

### Post by akuda on 2011-01-26
Hi,

I'm generally very content with Ubuntu 10.10.
There are only two things I am missing:
1) the hdaps-applet for gnome is not in official repository, but still can be googled, so no big deal here
2) my ThinkPad W500 is spinning it's fans with maximum speed all the time. I would like to silence them.
I googled, and I know of thinkpad_acpi and thinkfan.

In thinkfan manual there's a note, that I need to add some additional configuration, to prevent my hard drive from overheating. It's written, that I need to put a line to config pointing which sensor is a hard drive one, and add there some "artificial points".

The problem is, that I can't google a map of thinkpad w500, to know which number is the one for a hard drive sensor.

My question is:
1) how to properly (and safely) set up thinkfan on thinkpad w500 4062 model? OR
2) is there any other tool, that I can configure without having to guess :)

Regards,
akuda

---

### Post by gordintoronto on 2011-01-26
Have you looked at lm-sensors? You need to read a bit on the web site:
[https://help.ubuntu.com/community/SensorInstallHowto](https://help.ubuntu.com/community/SensorInstallHowto)
(That writeup is old, but I think it is still accurate. It might be worthwhile to Google the program's web site.)

---

