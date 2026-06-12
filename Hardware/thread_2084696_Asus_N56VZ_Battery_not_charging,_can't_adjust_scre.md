---
title: "Asus N56VZ: Battery not charging, can't adjust screen brightness with Fn key,..."
date: 2012-11-16
forum: Hardware
---

### Post by nguyenkien97 on 2012-11-16
Hello everyone. I've just installed Ubuntu 12.10 yesterday. I got latest updates, installed GNOME3 Shell, CompizConfig, and vietnamese plugin for Ibus. Everything works fine, but there are several problems:

1. Battery is not charging. Today when my battery is critically low (2%), i plugged charger in and the battery led kept blinking and left home. 3 hours later I came home and the led was still blinking. I turned the computer on and found that the battery is still 2%, which means my battery wasn't charged. When i remove and re-insert my battery, everything is normal. But sometimes I forgot and I don't want to bring a no-power laptop to class. Can anyone solve this?

2. Wrong battery status: The battery is 0% sometimes, and when I restart it, it's back to normal.

3. Can't change screen brightness with Fn + F5/F6 key

4. Wired device is not working (my wired adapter is  Atheros Communications Inc. AR8161 Gigabit Ethernet (rev 10) )

5. Fan keeps running full speed after suspend and when the battery is critically low even when i don't use anything that stress the system


// My English is bad so forgive me if there are any grammar/vocab errors :D

---

### Post by wildbat on 2012-12-06
+1 :sad:

---

### Post by WhiteWind4 on 2012-12-09
Hi! A have the same notebook and same bugs.
I just posted a bug report about battery (it`s a most annoying bug for me).
I am asking to join it and hope developers can solve it
[https://bugs.launchpad.net/ubuntu/+source/upower/+bug/1088146](https://bugs.launchpad.net/ubuntu/+source/upower/+bug/1088146)

I have (solved?) the bug with brightness. It`s a workaround with assigning any key combination to run xbacklight.
I assigned Ctrl+F5 to run "xbacklight -dec 10" and Ctrl+F6 to "xbacklight -inc 10"

I am wondering about numlock state, backlight and keyboard light states can be saved and restored after reboot. But it`s not so annoying as power bug.

---

### Post by flashno on 2013-04-25
Hey I have the same laptop as you guys, and while this is and older thread, I would like to provide a solution to the annoying power problem. 

[http://thecodecentral.com/2011/01/18/fix-ubuntu-10-10-suspendhibernate-not-working-bug](http://thecodecentral.com/2011/01/18/fix-ubuntu-10-10-suspendhibernate-not-working-bug)

This thread and fix solved the hibernation problem. Now when I close the screen, Ubuntu actually suspends. Hope this helps!

---

