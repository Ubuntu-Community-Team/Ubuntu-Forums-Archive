---
title: "ubuntu ATi woes!"
date: 2006-10-10
forum: Hardware &amp; Laptops
---

### Post by poserofalltrades on 2006-10-10
I a, really liking ubuntu, I really am. I have become so dreadfully sick of commercial operating systems that I truly want to make a full conversion to Linux. But, I am having problems making the switch.

With any Linux bistro, I have come to end up with the same problem: Abysmal support for ATi devices.

At least with ubuntu and the driver it has, I can run my native resolution of 1280x1024, but I can't get my dual-monitor set-up to work nor can I get anything GL to work, ever. Quick Example:
I go to change a screen saver and the system HARD LOCKS, becomes completely unresponsive whenever anything GL is displayed on screen, so the little preview box of the screen-saver crashes my system by itself. If the screen saver should play nice and I can do a "preview" of it full screen, it's artifact hell and ten a system lockup. CTRL-Z, nope. Have to hard reset and reboot.

So, pretty much I am restricted to single monitor and anything GL related will hard lock my system. Great. No XGL for me. No GL games using WINE. GR.

So, basically, I need to know if it is even AT ALL possible to get GL to work right on an ATi card. I know you can recompile the kernel with a new driver, but that is a little over my head and even when I had a friend do it for me, it still didn't work.

So, can anyone tell me if it is possible and what I need to do? It would be GREATLY appreciated if you could.

Thanks a bunch.

---

### Post by krisbowen on 2006-10-10
I have an ATi Radeon xpress 200M on my Ubuntu Laptop . I followed the Ubuntu wiki instructions for installing the driver and have had only one small issue that was my own fault...(when 3d acceleration kicks in my usb mouse stopped working..I directed it towards the wrong type of mouse I think)

located here
[http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide)

---

### Post by dbott67 on 2006-10-10
You can also download the latest ATI drivers from the ATI website.  What kind of card & what sort of system specs do you have?

Read my post here about getting ATI working on Radeon x1400:
[http://www.ubuntuforums.org/showthread.php?t=274915](http://www.ubuntuforums.org/showthread.php?t=274915)

Follow steps 5 & 6.

-Dave

---

### Post by poserofalltrades on 2006-10-10
Specs:

Radeon 9700 Pro (128mb)
AMD Athlon XP 2500+ (OC@ 2.2ghz)
1gb PC 2700 RAM

The old girl is showing her age, but I am confident it could run Beryl and aiglx/xgl pretty well.

Hell, it can take the abuse of Vista's Aero without a sweat.

---

### Post by poserofalltrades on 2006-10-17
Okay! So, I got XGL and Beryl up and running on my machine. I hit some speed-bumps on the way but I got it working.

There is only one major things I can think of that is a problem.

Whenever I launch an app, gnome does that animation (kinda like the old Mac OS) that goes across the screen. It bogs my system hard. The same thing can be said of resizing windows and minimizing/maximizing. Am I doing something wrong I don't know about?

---

