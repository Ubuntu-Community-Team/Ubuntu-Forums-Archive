---
title: "Panasonic DP-1510P"
date: 2012-11-05
forum: Hardware
---

### Post by ianhawke on 2012-11-05
Hey guys,

my issue regards ndiswrapper mainly. I'm trying to setup this printer

Panasonic DP-1510P

which is setup with an LPR queue on our work network. I went on the Panasonic website and I downloaded the Windows 32 bit driver.

When I run ndiswrapper the output is this

```

root@alessandro-TravelMate-8372:~/Desktop/dg2lviai090319# ndiswrapper-1.9 -i PFXSETUP.INF
installing pfxsetup ...
couldn't find install directive: "Panasonic DP-1510P"   = Pan15PIT.PFD
couldn't find install directive: "Panasonic DP-1810F"   = Pan18FIT.PFD
couldn't find install directive: "Panasonic DP-1810P"   = Pan18PIT.PFD
couldn't find install directive: "Panasonic DP-2010E"   = Pan201IT.PFD
root@alessandro-TravelMate-8372:~/Desktop/dg2lviai090319# 

```

Do you have any ideas? I tried looking for this everywhere, but it seems no one has the "couldn't find install directive" issue. What could this mean? Should I modify the driver somehow?

Thank you for any and all help!

-ianhawke-

---

### Post by ianhawke on 2012-11-06
Anyone got a clue on this issue? I'd really need some help, thank you!:confused:

---

### Post by baracco on 2013-10-27
On the Panasonic site I don' find the ubuntu driver for the DP-1510P. Where did you find it ?
Could you please help me ?
Thank you.

---

### Post by coffeecat on 2013-10-27
@baracco, a few points.

1 - I don't think there is a Linux driver for this printer. It is not listed in the Panasonic website (that I can find) nor in the OpenPrinting database:

[http://www.openprinting.org/printers/](http://www.openprinting.org/printers/)

2 - The OP has not logged in since November last year - you are unlikely to get a response from them.

3 - The OP does not mention a Linux/Ubuntu driver at all. They refer to the Windows driver and ndiswrapper, which won't work. Ndiswrapper is for using Windows wireless drivers in Linux. 

I fear that your printer may not be suitable for Linux (Ubuntu).

---

