---
title: "[SOLVED] Multiple Printer instances"
date: 2008-11-03
forum: Hardware
---

### Post by sydbat on 2008-11-03
I hope I am posting in the right board.

I installed Hardy onto my dad's box because he decided had had enough of Windows (he's 81 and learning anew - YAY for my dad!). At the same time he bought a new HP all in one on my recommendation because HP products just work with Gnu Linux. Installed the hplip driver from HP (sourceforge to be exact) and everything works great.

I get home (dad lives in BC and I'm in Alberta - about 1000km from each other) and he calls saying his printer won't print. I remote into his box and find there are at least 4 HP printers all named the same with 1, 2, 3. (ex. hp_blahblah - 2, hp_blahblah - 3). I had set up the HP as default and tested it before leaving.

He also has a Cannon printer that (amazingly) works well.

Is it possible that the 2 printers are in conflict, creating multiple instances of the HP printer?

To add - he turns his printers off when not in use. Can turning the HP on and off create the multiple printers?

Thanks in advance for your help. Let me know if you need more info.

---

### Post by sydbat on 2008-11-07
I know it's been 3 days with no answer, but I would like to know what to do. I have seen this on Windows boxes and simply attributed it to some Microsoft glitch. Seeing it on an Ubuntu box makes me wonder if it is something my father is doing that might create these "extra" printers.

Have any of you encountered this before? If so, how did you fix it? Can you just ignore the extra printers? Do I have to reinstall the driver?

I can remote easily into his box and fix whatever, I just need to know what your suggestions are to solve this problem.

Again, thanks in advance for your help.

---

### Post by gpsmikey on 2008-11-07
I have seen something similar before and was related to a printer that was plugged into a usb hub and the connection got moved to a different port on the hub.  It has also happened when there was no hub involved, just by moving the printer between different usb connectors on the pc (essentially the same thing).  This was in windows XP, but it has the same feel to it.

Hope that helps
mikey

---

### Post by sydbat on 2008-11-07
I never thought of the USB hub. It is an older box (sorry, I do not really know the specs...AMD Sempron and 512MB RAM) and the hub is USB 1.1. Could that be the problem? Turning the printer on/off tells the hub that it is a new printer each time?

---

### Post by gpsmikey on 2008-11-07
I would not expect turning it off and on to cause a new instance, but if the plug were plugged into different usb ports, (at least in XP on  my machine) it seemed to think it was a new printer.  You might see which one of the "multiples" you really can print to :)

mikey

---

### Post by sydbat on 2008-11-12
Had my dad switch from the USB hub to a front USB port and it stopped reading the printer as new each time. Thank you for your help. No more multiple printers!

---

