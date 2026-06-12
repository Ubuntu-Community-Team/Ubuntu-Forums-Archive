---
title: "How do I Power off the USB printer ?"
date: 2009-12-15
forum: Hardware
---

### Post by doswald on 2009-12-15
Hi all,

I support about 45 Ubuntu machines where they are shutdown nightly - depending on the user (done with cron).

Many of these machines have a USB printer attached to them (mostly HP and a few Canons). When the machines are powered up (and if the printers are powered off) the printer will automatically get powered on (so far so good).

The managers are asking if the USB printers can get powered off when the system(s) gets powered off. (darn tree huggers).

Initially I thought - who cares... 
But later I found out - because of travel schedules, these USB printers are sometimes powered up for a month without the system being used !

( OK - not such a unreasonable request anymore ).

The systems have a simple cron job which powers them off (/sbin/poweroff) - when required.

Im perfectly fine with setting up another cron job to power off the printer (before I shut the system down). 

But what do I need to run/call/execute in order to do this ?

Thanks in advance - Dave

---

