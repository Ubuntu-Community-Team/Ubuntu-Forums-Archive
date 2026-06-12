---
title: "uswsusp - strange behaviour on different ways of resume"
date: 2008-01-22
forum: Hardware &amp; Laptops
---

### Post by mclusky on 2008-01-22
I used s2ram -f command (uswsusp) to suspend and successful resume PC until I had to reinstall Ubuntu. After that PC goes to suspend mode, and it successfully resumes only when I use Power Button to resume.
But usually I need to resume PC with ACPI Alarm (using similar syntax): 
```
sudo sh -c 'echo "+00-00-00 01:30:00" > /proc/acpi/alarm'
```
In such case suspending goes fine, but automate resuming stops after few seconds. The last message in /var/log/massages and /var/log/kern.log states:
> Enabling non-boot CPUs ...
My MB is MS-7145, AMD Semron 3000+, BIOS supports ACPI, suspend method mode is set to 'auto'. Before reinstalling Ubuntu there was no problem with s2ram -f.

---

### Post by mclusky on 2008-01-26
I've found the reason for that strange behaviour: it was hardware related problem, caused by malfunction. I've replaced MB with another one, and everything is fine...

---

