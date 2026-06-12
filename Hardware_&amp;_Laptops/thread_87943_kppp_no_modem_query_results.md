---
title: "kppp no modem query results"
date: 2005-11-09
forum: Hardware &amp; Laptops
---

### Post by coolclassic on 2005-11-09
I have an external trust modem 56k (not winmodem) which I am trying to configure. Both pppconf and kppp reconise the modem but fail to connect, wvdial does not see the modem. Whilst querying the modem in kppp it comes up with no results i.e. no ATI codes. So I am assuming this could be the problem.

The modem is reconised as /dev/ttyS1 by both packages.

One other thing I have noticed is no IRQ is allocated for serial is this a problem?

---

### Post by m4ng0 on 2005-11-16
For wvdial, try:
sudo wvdialconf /etc/wvdial.conf

It would be useful to have more details. Can you post the output of
plog
after you have tried to connect?

---

