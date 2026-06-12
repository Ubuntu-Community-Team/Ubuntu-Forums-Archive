---
title: "hibernate wakes immediately in 9.10 on Thinkpad X40"
date: 2009-10-29
forum: Installation &amp; Upgrades
---

### Post by mikeh on 2009-10-29
Have a clean install of 9.10 on Thinkpad X40.
Suspend-to-RAM works after patch to fix backlight problem [https://bugs.launchpad.net/bugs/417599](https://bugs.launchpad.net/bugs/417599)

But hibernbate does not work. The system comes back on again, without a BIOS "reboot".

This looks like the relevant part of the log:

Oct 30 10:21:49 moon kernel: [ 2826.280710] PM: Creating hibernation image:
Oct 30 10:21:49 moon kernel: [ 2826.284007] PM: Need to copy 124550 pages
Oct 30 10:21:49 moon kernel: [ 2826.284007] PM: Hibernation image created (124550 pages copied)
Oct 30 10:21:49 moon kernel: [ 2826.284007] Extended CMOS year: 2000
Oct 30 10:21:49 moon kernel: [ 2826.284007] ACPI: Waking up from system sleep state S4

So it doesn't seem to be writing the hibernate image to disk.
Any ideas where I should be looking or terms to google?

---

### Post by running_rabbit07 on 2009-10-29
> **mikeh said:**
> Have a clean install of 9.10 on Thinkpad X40.
Suspend-to-RAM works after patch to fix backlight problem [https://bugs.launchpad.net/bugs/417599](https://bugs.launchpad.net/bugs/417599)

But hibernbate does not work. The system comes back on again, without a BIOS "reboot".

This looks like the relevant part of the log:

Oct 30 10:21:49 moon kernel: [ 2826.280710] PM: Creating hibernation image:
Oct 30 10:21:49 moon kernel: [ 2826.284007] PM: Need to copy 124550 pages
Oct 30 10:21:49 moon kernel: [ 2826.284007] PM: Hibernation image created (124550 pages copied)
Oct 30 10:21:49 moon kernel: [ 2826.284007] Extended CMOS year: 2000
Oct 30 10:21:49 moon kernel: [ 2826.284007] ACPI: Waking up from system sleep state S4

Any ideas where I should be looking or terms to google?

File a new bug?

---

### Post by mikeh on 2009-10-29
> **running_rabbit07 said:**
> File a new bug?

Don't think I understand it enough to usefully file a bug, which is why i posted on forums first. That wrong?
 Or even know where - would launchpad be the best place? Or is it a kernel issue?

---

### Post by running_rabbit07 on 2009-10-29
> **mikeh said:**
> Don't think I understand it enough to usefully file a bug, which is why i posted on forums first. That wrong?
 Or even know where - would launchpad be the best place? Or is it a kernel issue?

Launchpad would be a good place to do the bug report.

This is the right place to ask for help, please forgive me if I implied otherwise.

I don't know how to fix that issue, but hopefully someone who does will find this post soon.

Best of luck to ya.

---

### Post by TheForumTroll on 2009-10-29
Launchpad users should help you get the information needed if something is missing or send the bug futher up the chain if that is what it takes :)

[https://help.ubuntu.com/community/ReportingBugs](https://help.ubuntu.com/community/ReportingBugs)

---

