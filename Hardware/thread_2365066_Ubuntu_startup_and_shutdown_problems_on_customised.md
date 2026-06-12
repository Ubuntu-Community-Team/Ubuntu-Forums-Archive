---
title: "Ubuntu startup and shutdown problems on customised machine."
date: 2017-07-02
forum: Hardware
---

### Post by naveen-panwar27 on 2017-07-02
I have ubuntu 16.04 LTS which I have been using for quite some time on my laptop.

I have installed the same on my new Desktop Machine which has following configuration.

Intel Core i5 @ 7400 CPU
Graphics Kabylake GT2

I have the Biostar Racing Motherboard

I'm having problems on startup, shutdown, reboot, applications close unexpectedly even when I succeed to login.

I have to restart the Machine several times with Power Switch because sometimes 
the startup freezes on purple screen,
sometimes on ubuntu logo
sometimes with kernel panic
even the shutdown freezes
and many more things

is there something I do here, where should I check what is wrong?
how do I resolve these issues, please point me in right direction.

---

### Post by sp40140 on 2017-07-02
You can search the logs for details of the crash. (/var/log). It will be quicker / easier if you look just after the issues you mention.
Possible causes from _gut feeling_ in the order of priority:1] install didn't go well. 2] Faulty RAM 3]HDD problem 4]inadequate power supply 5] issue with mobo.

---

### Post by naveen-panwar27 on 2017-07-02
Hi sp40140,

thanks for checking in can you please suggest any options for possible diagnostics?

Would be much appreciated.

Thanks

---

### Post by gordintoronto on 2017-07-02
Your hardware is newer than your OS, which often leads to problems. I suggest 17.04.

---

### Post by naveen-panwar27 on 2017-07-04
Hi Guys,

Thanks everyone for helping out it turns out that one of the two rams were faulty I removed one and everything works like a charm.

Anybody else having the same problem can try this also.

Best Regards

---

