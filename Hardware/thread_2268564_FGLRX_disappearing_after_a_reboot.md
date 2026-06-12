---
title: "FGLRX disappearing after a reboot"
date: 2015-03-09
forum: Hardware
---

### Post by samuel.castledine on 2015-03-09
Hi,

So I've recently set up a  machine that has an AMD Raedon HD7770 Graphic card installed.

I decided to try the new Omega drivers (14.12) from AMD, they installed fine and I could run fglrxinfo after installation  to check that they were working. I then ran amdconfig --initial to create the configuration file for the new drivers.

However after a reboot I ran fglrxinfo again and got command not found.

Anyone else experiencing this? Any ideas on making the drivers stick?

Ubuntu 14.04.
Asus Raedon HD7770 2Gb

Sam

---

### Post by Keith_Helms on 2015-03-09
I can't help you if the command is really gone, but could this just be a path problem?

Try

**find / -name fglrxinfo 2>/dev/null**

and see if the command is located.

---

### Post by samuel.castledine on 2015-03-11
It couldn't find the command :( I think this must be a configuration conflict error with the new Omega drivers.  Going to close this thread now as I've switched to the open source drivers now anyway.

---

### Post by Mark Phelps on 2015-03-11
I can tell you that's not standard behaviour.  I installed the fglrx drivers recently and can still run the fglrxinfo command.

However, I chose the option to build release-dependent packages, and that was a LOT more work than I remember in the past.  Took me four passes to get all the dependencies finally installed.

---

