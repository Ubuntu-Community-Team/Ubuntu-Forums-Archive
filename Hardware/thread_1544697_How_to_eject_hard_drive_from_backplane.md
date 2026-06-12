---
title: "How to eject hard drive from backplane?"
date: 2010-08-02
forum: Hardware
---

### Post by pneumatic on 2010-08-02
I've done some reading and discovered a number of commands (hdparm -Y, sdparm --command=stop) to spin down the hard drive so that it can be ejected from a backplane and none of them worked.  Then I found "sg_start --stop" and that works with one problem - the drive spins right back up immediately.

How do I stop a drive permanently so that I can eject it?

---

### Post by pneumatic on 2010-08-02
Okay - potentially disregard.

[http://tldp.org/HOWTO/archived/SCSI-Programming-HOWTO/SCSI-Programming-HOWTO-4.html](http://tldp.org/HOWTO/archived/SCSI-Programming-HOWTO/SCSI-Programming-HOWTO-4.html)

I discovered this and am able to verify that a device disappears with a "remove-single-device" echo command.  In the morning, I will pull some drives to ensure that everything operates as desired.

---

### Post by pneumatic on 2010-08-03
Okay - that appears to do it.  It does not spin the drive down but I can safely unplug and replug drives to the backplane without panics or errors of any sort.

Can I mark this "solved" or does someone else have to do that?

---

