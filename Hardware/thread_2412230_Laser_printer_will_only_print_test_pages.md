---
title: "Laser printer will only print test pages"
date: 2019-02-09
forum: Hardware
---

### Post by Zobeid on 2019-02-09
The printer in question is a Brother HL-L2300D, and I am running the most recent Ubuntu MATE here.  I can go into Control Center and the "Printers" program, select my printer, and then hit the "Print Test Page" button, and it prints out the Ubuntu test page.  I just can't get it to print anything else, in other programs!  (Specifically, I've tried using GIMP and Firefox.)

It appears to accept the print jobs.  The job count increments, and the printer flashes its "ready" light for several seconds as if receiving data, but it never starts actually rolling out a page.

This printer was working until recently.  I don't think anything I did to the system could have messed it up.  In fact, a couple of days ago I wiped and re-installed Ubuntu MATE (for unrelated reasons), and the printer behavior remained unchanged.

---

### Post by ank2 on 2019-02-10
Anything interesting found in **/var/log/cups/error_log** ?

---

### Post by Zobeid on 2019-02-10
I did find a lot of these…

E [09/Feb/2019:19:08:36 -0600] [cups-deviced] PID 2545 (gutenprint53+usb) stopped with status 1!

---

