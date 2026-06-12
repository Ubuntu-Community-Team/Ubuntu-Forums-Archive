---
title: "Dead after time"
date: 2008-05-16
forum: Hardware
---

### Post by weaver4 on 2008-05-16
I am using HH (on a desktop unit) and it works perfectly when I am using it, but if I walk away for a few hours about 20% of the time when I come back the unit is dead.  I press the spacebar and the screen will not come back on.  When it is in this mode it is not just the display since the unit disappears from the network as well.

I don't know where to start to resolve this problem.  This hardware runs WindowXP just fine so I don't think it is a memory or other hardware problem.

I thought it might be related to the display, this motherboard is a Mini-itx motherboard from that has both a vga display and lcd display hardware on the board.  I would like to disable the lcd driver in Ubuntu for the LCD display to see if that resolves the problem, but I don't know how to do that.

I look in the log files and I don't see any errors, but I do see that the unit may work for 5 to 20 hours before it goes dead.

The board uses a standard Intel mobile processor and a the Intel 945GM & ICH*7M chipset.  Nothing special.

I have the screen saver on, but I never enable the Standby mode.

Help Please!

---

### Post by weaver4 on 2008-05-16
Bounce

---

### Post by weaver4 on 2008-05-20
Ok, I think I have found the problem.  I used synaptic to uninstall FireFox-3 and installed FireFox-2.

Under these conditions my Computer would generally lock up with 5-24 hours.

> Leave Firefox-2 running.

> and with an Adobe Flash object running inside of Firefox-2.

> and the Monitor was in the low power mode.

> and standby mode disabled.

Under the same conditions with Firefox-3 my computer does not lock up.

---

### Post by weaver4 on 2008-05-21
Well I was wrong.  After 3 days it failed again in the same fashion.

After working on this problem for 2 weeks I give up...back to Windows.

---

