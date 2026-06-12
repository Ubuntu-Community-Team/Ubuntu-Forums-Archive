---
title: "Acer Travelmate 3200 ACPI issue"
date: 2007-06-02
forum: Hardware &amp; Laptops
---

### Post by geco on 2007-06-02
Hi everybody, I'm running Feisty Fawn from an Acer Travelmate 3200 with *almost* no problems.
I dist-upgraded to the last kernel (2.6.20-16) and I **lost** my acpi informations about my battery/AC plug.
This fact is quite strange: only 2.6.20-15-generic kernel finds the battery, 2.6.20-15/16-386 and 2.6.20-16-generic kernels doesn't recognize it.
I compiled/debugged my DSDT with Intel iasl with no results and I feel a little bit lost.

I also noticed that with the new kernel my partitions change from /dev/sda* to /dev/hda*

Any idea/suggestion????

Thank you in advance.

---

### Post by youShotWhoInTheWhatNow on 2007-06-04
Hello,

I am having the same issue on my Acer Aspire 1680. The 2.6.20-15 kernel works fine, but the 2.6.20-16 does not seem to recognize my battery. My /proc/acpi/battery directory is empty when i boot into the newer kernel.

---

### Post by youShotWhoInTheWhatNow on 2007-06-04
Geco: you might want to join in on the bug report at: [https://bugs.launchpad.net/ubuntu/+bug/117504](https://bugs.launchpad.net/ubuntu/+bug/117504)

---

