---
title: "Fans disabled by software?"
date: 2008-09-17
forum: Hardware
---

### Post by rbolio on 2008-09-17
Hi!
 thanks for reading! 
Heres is my issue: Lateley ive noticed that my computer has been getting a little TOO hot! (5 C° would be the average in both procesors and CPU) 

The problem is taht ive noticed that the laptop fan is taking too much delay to ignite (or not ignitigin at all =X) 
Ive tried to keep it on at all times, but ive found that my dell wont allow that..

So...the question is; is there anyway to force fan to be on all the time (or make it start at colder temps...not 53°C.... )

Thank you for your time
ps. I have a Dell Inspiron E1050 (also known as the BIG 6400 xD) 

Thanks again!

---

### Post by bravo351 on 2008-09-17
Hotwire!

An old juryrig I pulled on my last comp, a Compaq Presario SR2163WM, when I arced the motherboard and fried my sys fan.  I had 4 channel outputs off my powerbox, and only 2 drives to power, so I took Red (constant positive) and Black (negative) off of channel 3 and hopped them to the sys fan.  It was annoying to have to press F2 every time I booted up, but the sys fan kept constant power.

Hope this helps.  And BTW, you may want to consider upgrading to an intercooling unit; much more efficient than a fan!

---

### Post by rbolio on 2008-09-17
but theres no reason for my fan to have burnt (or died?) ive never opened my laptop and it's pretty well cared for.....

and like i said, it turns on at 53°C (aprox), brings the pc temp down to 38, and then turns off.... i mean it does the job; but i dont like seeing my laptop at a constante temp. of 50....is that even good for the laptop?

---

### Post by ju2wheels on 2008-09-17
I recall reading somewhere that Ubuntu doesnt enable the fan on all laptops by default. I know specifically for my Thinkpad T42 it didnt because it got extremely hot. I had to modify the boot parameters in some file to get it to always enable my fan. 

If your fan is on you should be able to cat it from somewhere within the /proc tree. For example once I enabled it on my machine, I could do the following to see it was enabled:

```

> cat /proc/acpi/ibm/fan
status:		enabled
speed:		2878
level:		auto
commands:	level <level> (<level> is 0-7, auto, disengaged, full-speed)
commands:	enable, disable
commands:	watchdog <timeout> (<timeout> is 0 (off), 1-120 (seconds))

```

It was not possible to ge this information before enabling it, as it would just return 0. I would recommend looking up whether or not you need to enable anything for your laptop fan. Im not sure if this is the case for desktops though.

---

