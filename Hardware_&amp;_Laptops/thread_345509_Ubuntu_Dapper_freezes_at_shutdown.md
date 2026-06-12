---
title: "Ubuntu Dapper freezes at shutdown"
date: 2007-01-24
forum: Hardware &amp; Laptops
---

### Post by silas_irl on 2007-01-24
Yet another Ubuntu freezes on me at shutdown thread... :D

Just installed Dapper on my laptop (HP Pavilion DV2000), and it seems to be working fine for a day or two, then I noticed when shutting down that on the graphical screen it gets 50% and the last message is "Shutting down RAID services", then a text login screen appears and it freezes.  At this stage I can do one of two things, hard shutdown or the Alt+SysRq+rseiub combination.

I've had a look at the system logs and there not too helpful, or more that I'm not too experienced with the most technical bits of linux kernel shutting down, but there were a few things about ACPI (which I know is to do with power management).

I also noticed that the kernel did not have APM built into it.  Which I'm starting to think is possibly a factor.  As without it the laptop won't sleep, susped, hibernate correctly, or so I've read.

I just don't get why it was shutting down for the first few days and then suddenly stopped. 

Does anyone have any heads up on what might be causing it?

It's really a bit of a pain.

---

