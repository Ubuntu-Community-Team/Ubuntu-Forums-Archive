---
title: "Hoary broke ATI Radeon IGP 340M driver"
date: 2005-04-26
forum: Hardware &amp; Laptops
---

### Post by nadav on 2005-04-26
After installing Hoary I found that the system runs into a live-lock after a few minutes of using. Looking into the log I found this:

On Xconf.log
"(EE) RADEON(0): FIFO timed out, resetting engine..." 
multiple times

I had no problem with warty and also when I upgraded to hoary until about a month ago. I only got this on a fresh install. I believe that the bug was introduced within the last month 

My hardware:

0000:01:05.0 VGA compatible controller: ATI Technologies Inc Radeon IGP 340M (prog-if 00 [VGA])
        Subsystem: Hewlett-Packard Company: Unknown device 002a
        Flags: bus master, stepping, fast Back2Back, 66MHz, medium devsel, laten 

default configurations, i.e dri enabled
Acceleration works just fine when it dont hangs. 

-Nadav Rotem

---

### Post by alastair on 2005-04-26
If you do a Google search for this error, there are a few hits. I did not trace to see a resolution, if there is one. You could try the "vesa" driver, or do more searching and see if you can find anything more out (or revert to Warty until the next rev. of Xorg?).

[http://www.google.co.uk/search?q=radeon+%22FIFO+timed+out,+resetting+engine...%22&hl=en&lr=&start=10&sa=N](http://www.google.co.uk/search?q=radeon+%22FIFO+timed+out,+resetting+engine...%22&hl=en&lr=&start=10&sa=N)

---

### Post by nadav on 2005-04-26
I think I found a workaround. 

If I set the card's shared memory back to the defaults in the bios the problem does not occure.

---

