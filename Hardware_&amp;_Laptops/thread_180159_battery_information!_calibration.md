---
title: "battery information?! calibration?"
date: 2006-05-21
forum: Hardware &amp; Laptops
---

### Post by snipe122 on 2006-05-21
It seems that my battery percentage monitor in dapper works, but the time is always wrong... sometimes it says I have 8 hours left ;) would be great... can you calibrate this in some way so that it works right?

and: can I say somewhere that when its 3 % left it should hibernate? like in windows?


greetz
snipe

---

### Post by glinsvad on 2006-05-21
In Dapper there should be a menu item called "Power Management" somewhere... don't remember exactly 'cause I'm at on Breezy machine right now.

Anyway, it's in the Dapper specs under [power-management-configuration]("https://launchpad.net/distros/ubuntu/+spec/power-management-configuration")... so it must be supported somehow :)

My bat-stat is also mostly wrong about time left, but I think it's just a calibration thingy. Maybe running on power supply while battery is mounted makes it worse?

---

### Post by snipe122 on 2006-05-21
under powermanagement there you cant tell when it goes to hibernate... at least not in percentage... just for time... and the time is always wrong so it goes earlier than it has to into hibernate...

---

### Post by luibh on 2006-06-03
My HP ze4400 has the same problem. Currently 20 minutes past the popup window that warns the computer is going to shutdown due to lack of power. At first I thought maybe something was causing Dapper to drain the power, but now I see its not actually draining the battery. The monitor just thinks it is. Seems to be a somewhat common problem with laptops.

---

### Post by chris.raighn on 2007-02-13
I have kind of the same problem on my Toshiba Satellite. It will say that I have 2 minutes remaining also. I just disable the shutdown action when it reaches "critical". By doing this, it somehow fixes it. Also, I get about 30-40 percent more battery life with Ubuntu.

C.R.

---

