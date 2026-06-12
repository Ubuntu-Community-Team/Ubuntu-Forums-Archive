---
title: "emachine shutting itself off"
date: 2008-08-28
forum: General Help
---

### Post by Matthew T. on 2008-08-28
I'm running an emachines T5234 with an AMD Athlon 64x2 4200+ processor and 2 gigs of RAM. This afternoon, the computer suddenly turned itself off. No shutdown process, just instant power loss. My wife booted it back up a few hours later and it ran fine. 

CPU temp shows 104. She turned it off a few days ago by holding in the power button (didn't realize I had a virtual machine on desktop 2, causing the shutdown to hang). The system ran fsck went it came up next time and it found no errors. I just upgraded to kernel 2.6-.24-19. 

Here's the syslog from right before it occurred:

Aug 28 13:17:01 ubuntu /USR/SBIN/CRON[7566]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Aug 28 13:41:21 ubuntu -- MARK --

Help, please.

---

### Post by srt4play on 2008-08-28
> **Matthew T. said:**
> CPU temp shows 104

Celsius or Fahrenheit?

---

### Post by Matthew T. on 2008-08-28
That would be Fahrenheit.

---

### Post by Predator106 on 2008-08-28
That's all that's in the log? There isn't anything of interest that I know of. Is there anything before that, of possible interest. If not, I guess it's either a temperature issue, or a PSU issue, just my opinion, it doesn't sound like anything from linux, but I could of course, be mistaken.

---

