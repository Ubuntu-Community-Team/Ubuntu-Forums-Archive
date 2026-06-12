---
title: "Debugging ACPI Issues on Edgy Stock"
date: 2007-04-18
forum: Hardware &amp; Laptops
---

### Post by Nik_Doof on 2007-04-18
I've recently aquired an issue with my Ubuntu Edgy installation in that at around the same time every night the system fires a ACPI critical trip point and shuts down. The error message in /var/log/messages is rather useless but it points me towards a ACPI system issue. 

> localhost kernel: ACPI: Critical trip point

As another unusual side effect it seems to have happend at around the same time for the last two nights (around 22.50), i've checked for high load crontabs but nothing seems to run at that time. I've now setup a temp monitoring script dumping /proc/acpi info at regular intevals in the hope to find something failing.

Is there any way to enable further acpi debugging in the kernel? The above message is all I get before the usual shutdown entries. Also, would the stock ACPI in edgy monitor a nvidia card temp sensor?

---

