---
title: "How can I find the print queue name for my printer?"
date: 2013-12-20
forum: Hardware
---

### Post by hodad on 2013-12-20
There are lots of commands for printing, but I can't seem to find one that returns the name of my print queue.  I need the print queue name to force a print to the printer  with the lp command (for printer troubleshooting).

---

### Post by Keith_Beef on 2013-12-21
Try lpstat -a; this should return a list of all declared print queues, like the example shown from my system, below.
```

$ lpstat -a
Dymo-Label accepting requests since Sun 12 Aug 2012 06:22:34 PM CEST
DYMO-LabelWriter-DUO-Label accepting requests since Sun 12 Aug 2012 06:22:38 PM CEST
Stylus-Photo-890 accepting requests since Tue 17 Dec 2013 07:28:52 AM CET

```

---

### Post by hodad on 2013-12-21
I did that and got:
...$ lpstat -a
Canon-MF4700-UFRII-LT accepting requests since Fri 20 Dec 2013 04:09:19 PM MST
...$ 
I had done that previously, but didn't know that that was the actual name of the print queue, I thought it was just the printer name.  So am I correct to assume that the actual print queue name is "Canon-MF-UFRII-LT"?

---

### Post by Keith_Beef on 2013-12-22
Try using that name to check the state of the queue; it should work, and what can go wrong?

```
lpq -PCanon-MF4700-UFRII-LT
```

Then use that name to send a job to the printer.

---

### Post by hodad on 2013-12-22
Sorry for delay - here's what I get.  Note that I've played around with reinstalling printer, so print queue name seems to have changed(See printscreen below ). 

When I print a file, or a test page, it's going into oblivion somewhere.  The job count id up to about 170 now, and none of them show up in the print queue when I click on the named printer (underSystem Settings).  Trying to figure out where they're going (?)

Would like to just get anything to print from the Linux pc, even garbage.   The printer is set up as a network printer, and is working fine under Windows, so I know it's not the printer itself. It has to do with the drivers provided by Canon.

---

