---
title: "How to find out BIOS, especial HPET info"
date: 2009-09-09
forum: Hardware
---

### Post by dcstar on 2009-09-09
I noticed that this question was unanswered in the archive forum, so the answer is to look for "rtc-cmos" entries in the boot-up section of your syslog file.

The old timer hardware only have "rtc" enties, hardware that supports HPET will have the "rtc-cmos" entries, and you should (apparently) set it to either 32 or 64-bit in your BIOS to match the O/S you are using (32-bit if you boot both).

---

