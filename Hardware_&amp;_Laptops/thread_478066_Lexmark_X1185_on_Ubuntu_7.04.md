---
title: "Lexmark X1185 on Ubuntu 7.04"
date: 2007-06-18
forum: Hardware &amp; Laptops
---

### Post by b1nary_w01f on 2007-06-18
Hi all,
I've been having a small problem with my printer. I'm using Ubuntu 7.04 and a Lexmark x1185 and the driver is not in the printer adding tool included with Ubuntu. I've tried a variety of other 1100 series drivers to see if any will work and have seen no results. if anyone has any ideas or information that could help it would be greatly appreciated. Thanks.

---

### Post by hummingbird59 on 2007-06-19
Have a look at [http://openprinting.org/show_printer.cgi?recnum=Lexmark-X1185](http://openprinting.org/show_printer.cgi?recnum=Lexmark-X1185).  It looks like your printer is supported.:)

---

### Post by b1nary_w01f on 2007-06-20
Thanks for the help, but no luck. I fallowed the directions listed at [http://ubuntuforums.org/showthread.php?t=49714&highlight=X1150](http://ubuntuforums.org/showthread.php?t=49714&highlight=X1150). and used the driver recommended in the link you sent, but still nothing. all my printing jobs just stop. eh, I'll just fiddle with it more. its most likely some small detail or instruction i missed or over read. If all else fails i have some other printers i can try. = )

---

### Post by stchman on 2007-06-20
> **b1nary_w01f said:**
> Hi all,
I've been having a small problem with my printer. I'm using Ubuntu 7.04 and a Lexmark x1185 and the driver is not in the printer adding tool included with Ubuntu. I've tried a variety of other 1100 series drivers to see if any will work and have seen no results. if anyone has any ideas or information that could help it would be greatly appreciated. Thanks.

Find a similar printer and use the z600llpddk-2.0 / z600cups-1.0 drivers.

---

### Post by b1nary_w01f on 2007-06-20
I am useing those dirvers, but still no luck. all my jobs just stop 15 seconds after they start.

---

### Post by hummingbird59 on 2007-06-20
This may be a long shot but have you tried uninstalling and reinstalling your printer using the recommended driver(s).  You might also try restarting cups:  type in a terminal: sudo /etc/init.d/cupsys restart.  I honestly don't know if this will help but may be worth a try.  A completely untechnical approach is also to physically unplug your printer from your machine, replug, restart cups and reinstall.  Sorry I can't be of more help.

---

### Post by b1nary_w01f on 2007-06-21
nope, still no luck. eh, I'll just see if i can use one of my other printers(this one never worked 100% of the time on windows ether, its uhhh...been dropped before...). Thanks for the help anyways.

---

