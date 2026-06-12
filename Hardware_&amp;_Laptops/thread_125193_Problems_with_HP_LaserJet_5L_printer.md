---
title: "Problems with HP LaserJet 5L printer"
date: 2006-02-03
forum: Hardware &amp; Laptops
---

### Post by sept00 on 2006-02-03
A few days ago my very trusty LaserJet 5L stopped working with Breezy. I'm not sure, but it could have been a package update after which it stopped. When I open the Print-Manager in Konqueror, the printer is there, I can configure it and everything. But when I give the command to print a page, the printer lights blink twice and the cups error log shows output like this:
```
I [03/Feb/2006:15:30:19 +0100] Adding start banner page "none" to job 2.
I [03/Feb/2006:15:30:19 +0100] Adding end banner page "none" to job 2.
I [03/Feb/2006:15:30:19 +0100] Job 2 queued on 'HPLaserJet5L' by 'thomas'.
I [03/Feb/2006:15:30:19 +0100] Started filter /usr/lib/cups/filter/pstops (PID 7635) for job 2.
I [03/Feb/2006:15:30:19 +0100] Started filter /usr/lib/cups/filter/foomatic-rip (PID 7636) for job 2.
I [03/Feb/2006:15:30:19 +0100] Started backend /usr/lib/cups/backend/parallel (PID 7637) for job 2.

```

No error, no permission problems, nothing.

I fired up a Hoary Live CD, which had the printer working basically out of the box, so I know it's not the printer that's broken. I have the "Foomatic/ljet4" driver installed.

Does anybody know what's going on? I'm very frustrated, as I have a lot of printing to get done towards the end of my semester. Thanks!

---

