---
title: "Spindown Harddrive"
date: 2005-11-26
forum: General Help
---

### Post by daller on 2005-11-26
Hi There,

I've got Breezy on my laptop (Dell Inspiron 8600)

My harddrive never spin down!

In hoary my harddrive spun down after some minutes of inactivity...

How do I enable this in Breezy?

---

### Post by bin on 2005-11-27
You can force this with hdparm - man hdparm the -S code but read carefully about the values of the parameter

-S     Set the standby (spindown) timeout for the drive.  This value is
              used by the drive to determine how long to wait  (with  no  disk
              activity)  before  turning  off the spindle motor to save power.
              Under such circumstances, the drive may take as long as 30  sec&#8208;
              onds  to respond to a subsequent disk access, though most drives
              are much quicker.  The encoding of the timeout value is somewhat
              peculiar.   A  value  of zero means "timeouts are disabled": the
              device will not automatically enter standby mode.  Values from 1
              to  240 specify multiples of 5 seconds, yielding timeouts from 5
              seconds to 20 minutes.  Values from 241 to 251 specify from 1 to
              11 units of 30 minutes, yielding timeouts from 30 minutes to 5.5
              hours.  A value of 252 signifies a  timeout  of  21  minutes.  A
              value  of 253 sets a vendor-defined timeout period between 8 and
              12 hours, and the value 254 is reserved.  255 is interpreted  as
              21  minutes  plus  15  seconds.  Note that some older drives may
              have very different interpretations of these values.

in light

bin

---

