---
title: "external monitor and Laptop Lenovo 3000 N100"
date: 2007-10-18
forum: Hardware &amp; Laptops
---

### Post by koniu1 on 2007-10-18
Hello all,

I have a question if someone knows how to solve the issue with connecting external monitor to the lenovo 3000 n100 laptop. 
I've got KDE installed.
 Thank's in advance for every answer

---

### Post by drorata on 2008-05-23
I would like to revive this thread, since I'm experiencing the same problem more or less. I managed to connect the external monitor using the following procedure:

1. Connect the external monitor

2. Add the following line to the xorg.conf:
                 Virtual		2000 800
under the "Display" subsection.

3. ctrl-alt-backspace in order to restart the desktop. It works almost good.

I'm having the following problems now:
1. The desktop on the laptop (1280X800, Lenovo 3000 N100) doesn't use the whole screen, only about two thirds of the upper left corner.
2. The resolution on the external monitor is: 1024X768 where it can support 1600X1050.
3. Last, and most annoying, it works in clone mode, i.e. the same output on both monitors. I DO want it to work in extended desktop mode.

Anyone has ideas for the solution?

Thanks in advance,
Dror

---

