---
title: "Driver for LG 24mp59g"
date: 2018-05-13
forum: Hardware
---

### Post by kilmar on 2018-05-13
Hello

I need help. I bought an LG monitor, but the cd inside the box is (i assume) only run at windows machine.
can anybody tell me what should I do to make the monitor run?

thanks for the help.

---

### Post by papibe on 2018-05-13
Hi kilmar. Welcome to the forum ):P

When you turn on your computer, the OS (Windows, Linux or other) asks the monitor for available resolutions, the monitor replies, and the OS chooses one. This process doesn't really require a special driver.

Are you having any resolution problem?
Do you have a graphic card? This driver is more important actually.

Regards.

---

### Post by kilmar on 2018-05-13
> **papibe said:**
> Hi kilmar. Welcome to the forum ):P

When you turn on your computer, the OS (Windows, Linux or other) asks the monitor for available resolutions, the monitor replies, and the OS chooses one. This process doesn't really require a special driver.

Are you having any resolution problem?
Do you have a graphic card? This driver is more important actually.

Regards.


Thank you for the reply @papibe
Hmm I don't know, when I plug in the monitor it says no signal..
I used Asus n56vj, and the graphic card is Nvidia GeForce 635m I guess

---

### Post by papibe on 2018-05-13
Do you have the Nvidia driver installed? If not open 'Additional Drivers' and install it from there, then reboot.

How are you connecting the monitor? HDMI, VGA?

Regards.

---

### Post by kilmar on 2018-05-13
> **papibe said:**
> Do you have the Nvidia driver installed? If not open 'Additional Drivers' and install it from there, then reboot.

How are you connecting the monitor? HDMI, VGA?

Regards.

Yes, I think I used the x.org one. Which one is better?
And I connected it via HDMI.

---

### Post by papibe on 2018-05-13
Could you open a terminal, run these commands, and post back the results? (you can copy/paste the text using your mouse)
```
lspci -nnk | grep -iA2 vga

lsmod | grep -iE 'nvidia|intel|fglrx|radeon|nouveau'

xrandr --q1

xrandr --q12

xvidtune -show
```
Regards.

---

### Post by kilmar on 2018-05-13
> **papibe said:**
> Could you open a terminal, run these commands, and post back the results? (you can copy/paste the text using your mouse)
```
lspci -nnk | grep -iA2 vga

lsmod | grep -iE 'nvidia|intel|fglrx|radeon|nouveau'

xrandr --q1

xrandr --q12

xvidtune -show
```
Regards.

thank you, actually after I restart my computer the monitor suddenly worked!
I don't know what is causing it to not working in the first place, but I will remember your advice when the trouble return.
thank you very much!

---

### Post by papibe on 2018-05-13
I'm glad your monitor is working well :)

Come here often, and have fun.
Regards.

---

### Post by kilmar on 2018-05-15
Thank you very much!
I hope I can learn a lot here!

---

