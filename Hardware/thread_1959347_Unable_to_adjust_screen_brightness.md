---
title: "Unable to adjust screen brightness"
date: 2012-04-15
forum: Hardware
---

### Post by caffeine. on 2012-04-15
I have an HP Pavilion dv6 laptop running Natty. The brightness controls work fine in Windows but never worked in Ubuntu. I finally installed Kamal Mostafa's patch that worked perfectly for a while, and then abruptly stopped working a few months ago. At that point I did something (unfortunately I don't remember what) and got it working again, but then two things happened:

1. My computer kept crashing (maybe once or twice a week for a few weeks) with a "Tainted" message and the name of the backlight patch; I don't remember exactly what the error was, but at the time the backlight controls continued to work so I didn't pay too much attention to it.

2. Today the backlight controls stopped working again altogether, and I can't figure out what to do to fix it-- this is a somewhat more pressing problem for me since my eyes can't take the current screen brightness and no other adjustments have worked. I think it might have to do with an apt-get update/apt-get upgrade I did recently, but I have upgraded before today and it's been fine, so I don't know exactly what might be causing it.

Any help would be very much appreciated.

Thanks!

---

### Post by Toz on 2012-04-15
You could try posting a comment here ([https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/568611]("https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/568611")) about your problem, but according to the comments at the end, this PPA is no longer being supported (I can't confirm this though).

It is possible that a kernel update borked your backlight. Have you tried booting with a previous kernel?

---

### Post by magtrask on 2012-09-21
I've had the brightness fn problem on my HP Pavilion dm3 with every ubuntu version including 12.04, until today.

Try following the suggestion at:
[HTML]http://www.techjail.net/solved-brightness-problem-in-ubuntu-12-04-precise-pangolin.html[/HTML]

---

