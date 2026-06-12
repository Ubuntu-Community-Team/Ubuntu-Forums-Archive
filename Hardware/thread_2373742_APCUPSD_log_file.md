---
title: "APCUPSD log file"
date: 2017-10-09
forum: Hardware
---

### Post by danik56 on 2017-10-09
Is there a way to configure APCUPSD to use a separate log file ?

---

### Post by SeijiSensei on 2017-10-09
See the EVENTSFILE and STATFILE directives in apcupsd.conf.

---

### Post by danik56 on 2017-10-15
> **SeijiSensei said:**
> See the EVENTSFILE and STATFILE directives in apcupsd.conf.

Thanks for the info. Is there a way to test the low battery shutdown procedure without waiting for the battery to drain?

---

### Post by SeijiSensei on 2017-10-15
> **danik56 said:**
> Thanks for the info. Is there a way to test the low battery shutdown procedure without waiting for the battery to drain?

Shut down the apcupsd daemon, then run "sudo apctest".  You'll get a menu of tests like this:

```

1)  Test kill UPS power
2)  Perform self-test
3)  Read last self-test result
4)  View/Change battery date
5)  View manufacturing date
6)  View/Change alarm behavior
7)  View/Change sensitivity
8)  View/Change low transfer voltage
9)  View/Change high transfer voltage
10) Perform battery calibration
11) Test alarm
12) View/Change self-test interval
 Q) Quit

```

I'm running a rather old version of apcupsd on a CentOS server, so the current menu may look different from that.

For a real test though, I would disconnect it from the power lines and let the battery drain.  In most instances we're only talking about twenty minutes or so.  Back up any critical data beforehand, of course, and don't leave any open files lying about.  Close any apps you're working with.

---

