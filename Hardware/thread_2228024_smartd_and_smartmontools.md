---
title: "smartd and smartmontools"
date: 2014-06-05
forum: Hardware
---

### Post by matt_symes on 2014-06-05
Hi all.

Can anybody tell me if the smartd daemon would cause a hard drive (both internal or external) that has spun down to spin up ?

I am thinking of installing it on a media server but i won't if it will spin up the drives whenever it does a smart test.

These drives spin down after 20 mins of non use to save power. I don't want then spinning up just for a smart test.

Kind regards

---

### Post by tgalati4 on 2014-06-05
SMART tests are performed at boot and depending on the drive after every few hours of power-on.  You would have to research the specific drive to determine the interval.  You should activate SMART on the drives so that errors get logged on the drive, otherwise you will never get a warning that there are problems.

For PATA drives (old style IDE's) there is a nocheck if sleeping directive:

> 

       -n POWERMODE[,N][,q]
              [ATA only] This ´nocheck´ Directive is used to prevent a disk from being spun-up when it is periodically polled by smartd.


I don't know how SATA drives are handled or if it is automatic.

```
man smartd.conf
```

I would start the *smartd* daemon and then with the case open, listen to the drives and see if they spin up when they are not being used.

I have a *freenas* server with several TB's of SATA drives and SMART is activated (and I even get emails when errors are found) and my drives seem to stay asleep.  So this may not be an issue.  But test it to convince yourself.

---

### Post by matt_symes on 2014-06-05
Hi tgalati4

Thanks for the reply.

SMART is enabled on all the drives so that is not a problem.

3 of the drives are internal  (SATA2) and 2 are external usb (one SATA2 and one SATA3 - running at SATA2).

Interesting switch for pata drives. I had not come across that.

I run manual smart tests on the drives once a month or so, but i have always spun the drives up by that point.

> I would start the *smartd* daemon and then with the case open, listen to the drives and see if they spin up when they are not being used.

This sounds like the way forward. I'll find the time to check them and report back.

> I have a *freenas* server with several TB's of SATA drives and  SMART is activated (and I even get emails when errors are found) and my  drives seem to stay asleep.  So this may not be an issue.  But test it  to convince yourself.

This is good to know. I hope it's the same with my external drives as well.

Kind regards

---

### Post by tgalati4 on 2014-06-05
External SATA drives may be problematic because power is supplied through the SATA channel and any changes in the idle/sleep state of the motherboard may affect the power state of the estata.  That might cause those drives to wake up whenever there is a change in the motherboard state.  esata's are really not designed for file server use, but for convenience in backing up systems and transfering files in a one-time fashion.  If you need more internal SATA ports, then I would suggest an internal SATA card.

---

