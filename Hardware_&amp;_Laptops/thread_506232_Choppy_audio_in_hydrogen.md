---
title: "Choppy audio in hydrogen"
date: 2007-07-21
forum: Hardware &amp; Laptops
---

### Post by jr.gotti on 2007-07-21
I just installed UbuntuStudio, and when i got jack running and booted up ardour or hydrogen, EVERYTHING that plays is choppy. It's unusable. What can I do to get that fixed?

---

### Post by 5-HT on 2007-07-26
You may find benefits from playing around with JACK's setup (easiest way is through qjackctl). One thing worth checking out and adjusting would be the number of periods per buffer (the sample rate and frames per period could then be adjusted to control latency keeping in mind system ressource utilization). Another thing would be to verify your I/O connections in JACK.
It might take some fooling around, but once you know which settings work on your system it's smooth sailing from there.
cheers,

---

