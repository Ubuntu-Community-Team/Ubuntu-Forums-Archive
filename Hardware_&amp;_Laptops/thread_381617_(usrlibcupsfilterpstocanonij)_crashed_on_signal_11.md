---
title: "(/usr/lib/cups/filter/pstocanonij) crashed on signal 11!"
date: 2007-03-11
forum: Hardware &amp; Laptops
---

### Post by Erlander on 2007-03-11
I have installed a Canon iP4300 printer using the driver for the iP4200 and this guide:

[https://help.ubuntu.com/community/HardwareSupportComponentsPrinters/CanonPrinters/CanonPixmaIP4200#preview](https://help.ubuntu.com/community/HardwareSupportComponentsPrinters/CanonPrinters/CanonPixmaIP4200#preview)

The printer will print a test page and will print from Open Office and the text editor but trying to print from Firefox produces the following error in the cups/error-log:

```
E [11/Mar/2007:16:49:15 +1100] PID 17217 (/usr/lib/cups/filter/pstocanonij) crashed on signal 11!
```

If I open the printer's job list the state of the print job is: "Stopped: job-stopped" but it will not resume.

I am relatively new to Linux and Ubuntu and would very much like some help.

Rob

---

### Post by Erlander on 2007-03-11
I think I have resolved this problem.

Searching here and elsewhere on the web I found that apparently there is a conflict in firefox configuration concerning paper size.  Changing from A4 to Letter got me going even though I'm using A4.

Further searching gave me this discussion:
[http://forums.xandros.com/viewtopic.php?t=27050&sid=c5bf86d36eaed76745030ec45d1d1e65](http://forums.xandros.com/viewtopic.php?t=27050&sid=c5bf86d36eaed76745030ec45d1d1e65)

I used the procedure there to change my default paper size back to A4

So far so good.  Fingers crossed that I didn't change anything else.

Rob

---

### Post by BlackSir on 2007-06-23
I've had a similar problem with pstocanonij crashed with signal 11 with official Canon PIXMA MP160 drivers installed on Canon PIXMA MP170 printer. Solution: delete ~/.cups/lpoptions - seems like pstocanonij doesn't like PageRegion or something...

---

### Post by nicolos on 2007-11-17
Thanks for the tip BlackSir, same crash problem with Canon Pixma MP600 driver, removing ~/.cups/lpoptions solved the issue too.

---

