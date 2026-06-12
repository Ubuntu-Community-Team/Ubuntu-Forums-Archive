---
title: "Novatel 5720 &quot;No Carrier&quot; Error"
date: 2008-06-25
forum: Hardware
---

### Post by jbentham on 2008-06-25
Hello,

I have an internal Novatel 5720 CDMA modem that has been activated and tested on WXP, and to which I can query using KPPP, but each time I try dialing out, I get "No Carrier" and cannot connect.

Previously on this same laptop (a Dell D820), I had used a Pantech PX-500 PCMCIA card without any trouble at all - good speed and connections, so I'm pretty sure KPPP and modprobe is set up correctly (I have the correct vendor and product numbers for the internal card).

So, since I can query the modem, but just can't get a carrier, what else can I check or do to troubleshoot?


Thanks!

---

### Post by phidia on 2008-06-25
You could install minicom and if you know the AT&T codes (just a few) for resetting the modem and calling out you can, hopefully, figure out what the problem is. [minicom man page]("http://linux.die.net/man/1/minicom")

---

