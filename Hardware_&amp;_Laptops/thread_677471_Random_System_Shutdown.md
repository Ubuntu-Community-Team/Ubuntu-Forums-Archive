---
title: "Random System Shutdown"
date: 2008-01-24
forum: Hardware &amp; Laptops
---

### Post by Salazar420 on 2008-01-24
Hello, everyone.

I am using the Gateway M520 series laptop (not sure which variant). My system specs include: Intel Pentium 4 3.06 ghz processor, 512 mb ram (likely generic), RV350 Mobility Radeon 9600 M10 Graphics card, BCM4306 802.11 b/g Broadcom wireless lan controller, etc...

I've been experiencing random system shutdowns. It is not unusual for these shutdowns to be accompanied by system "beeps." I am at a loss for reason, but I think it's best I note that the battery has been rendered broken by my system everytime I boot. It's wierd because, although the system deems my batter old or broken, with only 43% capacity capability, it still seems to hold a typical charge. 

Also, as a footnote, when I open my laptop screen it flickers, as if on the verge of giving up.

I'd really like to identify the source of these system shutdowns, and fix the problem therein. Anybody have any ideas?

---

### Post by eredhuin on 2008-01-24
A general debugging technique is to look to see if there's anything useful in your log files.

e.g. 

cat /var/log/messages

If you see some kind of "panic" statement from before your last reboot, there's a place to start.

Although it sounds like it could be dying hardware.

---

### Post by Salazar420 on 2008-01-27
Sorry about the belated reply. Anyway, the list is far too long to sift through. However, 'cat /var/log/messages | grep panic' showed me no results... I suppose this is good. So, "dying hardware?" Damn, that doesn't sound good; especially seeing as how I just bought the laptop, and got it for a once-in-a-lifetime good deal. Did I mention the screen's random checkered, colored blocks, or wierd streams of colors and scrambled images, much like when a satalite televisions goes all blocky and linear? Anyway, what would I do about dying hardware? Replace the pieces? Def got a broken battery....even though it still works -- just cause it says it's broken upon startup.. and the monitor looks as though it could die wihtin a few months... but what if it's the mobo or something? Trash the whole of it? Oh god.. I'm panicky... I don't want to loose "my precious." Btw, do you know why it says I have two cpus? my CPU Frequency Monitor says I have CPU 0 and CPU 1.

---

