---
title: "Serial issue after docking/undocking"
date: 2009-11-16
forum: Hardware
---

### Post by pwrdbyredhat on 2009-11-16
I'm running ubuntu 9.10 on Dell Latitude D810.  I have a serial port on back of laptop and back of docking station.  If I dock the machine and boot it up I can access my cisco devices through minicom or putty using /dev/ttyS0.  It also works fine if I boot the laptop undocked and plug into the serial port on the back of the laptop.

The problem is when the machine is docked and then I undock it and plug into the serial on the back of the laptop then open minicom or putty I just get a blank terminal.  Same thing happens if I'm using it undocked and then dock the laptop. 

It seems that once it is running and then you change being docked/undocked it kills the serial connection.

To fix this issue so far I've been having to restart the machine to get serial connection to come back.  Is there any solution or anyway I can reset the /dev/ttyS0 without having to do a full reboot or even a logout?

---

### Post by pwrdbyredhat on 2009-11-20
Bump for input.

---

### Post by metasyntax on 2009-12-02
Not a solution, yet anyway.  However I have the exact same problem with my D630.  I have some ideas that I'll try over the next couple of days.

meta

---

