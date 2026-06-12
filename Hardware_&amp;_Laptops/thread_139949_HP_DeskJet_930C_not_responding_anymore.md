---
title: "HP DeskJet 930C not responding anymore"
date: 2006-03-05
forum: Hardware &amp; Laptops
---

### Post by matthias_k on 2006-03-05
Hi,

since a couple of weeks, my printer does not work anymore. Yes, it DID work with Ubuntu Hoary and Breezy for almost a year, and then all of a sudden I can't print anymore.

The printer status is always reading: "Ready: open device failed; will retry in 30 seconds..."

I tried re-adding it, also in different ports, no luck. Switching from USB to parallel port back and forth also had no effect. The printer is definitely not broken in that it couldn't print anymore: I can trigger a test-page from the buttons at the printer, but it doesn't seem to be able to communicate with my computer anymore.

Any ideas?

---

### Post by 11hjpphty76lkjj on 2006-03-06
Disconnect the printer, then open a terminal window, and enter this command:

sudo tail -f /var/log/syslog

then reconnect the printer, post any errors noted.

Did you upgrade to Dapper?

Thanks!

Aaron

---

### Post by matthias_k on 2006-03-07
The log doesn't yield any useful information, it seems that the printer isn't detected anymore.

Is there a way to manually scan the parallel ports?

---

