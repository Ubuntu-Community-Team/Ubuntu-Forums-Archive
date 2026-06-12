---
title: "Screen brightness in too low"
date: 2008-04-24
forum: Hardware
---

### Post by haseeb on 2008-04-24
I have installed Hardy in my laptop Acer Aspire 5710. Everything goes fine (except two things).

* Touch pad is a **** now (like earlier versions). Anyway, I dont use it. So doesnt matter for me.

* Screen contrast is too low. With AC power it seems I am running on my battery. 

I did a try by changing gamma. But monitor is still without bright glossy look.. :-(.

Any suggestion on how to increase brightness contrast in the monitor ?

---

### Post by neonflx on 2008-04-25
i am having the same issue with an ASUS M50SV-A1 laptop, screen brightness is just too low to begin with, i tried using the nvidia panel after installing the drivers but it just don't work properly as the brightness is so low to begin with that adjusting brightness/contrast/gamma thru it does not work

---

### Post by fireman10 on 2008-04-25
I have problem too. After update from Ubuntu 7.10 to 8.04 on my notebook Asus U5F, when X start - display brightness very low (minimal level).
When notebook shutdown or reboot brightness still very low too.
Tested on gdm and kdm. 

Problem 2.

Wifi **automaticaly** turned **"ON"** when Ubuntu start.
It always turned "ON".

Ubuntu 7.10 have not this problems.
Resolved problems in 8.04: My notebooks Fn-keys work!

---

### Post by ]Nbx*cmD[ on 2008-04-25
ok found a solution for u guys using ASUS M50sv laptop.

The problem seems to be with the lihght sensor, which doesn't work properly.

First of all, take a torchlight and point it to the sensor (right to the right of the "ALTEC LANSING" writing on the top of your keyboard) and... voila! lights up!

Ok, here's the fix:

> 
$sudo su
#echo 0 > /sys/devices/platform/asus_laptop/ls_switch


This will put a 0 in the ls_switch file, telling your laptop to NOT use the light sensor, which will give you the control of your brightness back.

Hope it helps!

Taken from: [http://vip.asus.com/forum/view.aspx?board_id=3&model=M50Sr&id=20080411154124718&page=1&SLanguage=en-us](http://vip.asus.com/forum/view.aspx?board_id=3&model=M50Sr&id=20080411154124718&page=1&SLanguage=en-us)

---

### Post by nevcos on 2008-11-03
Extremely usefull! My eyes thank you a lot :)!

---

