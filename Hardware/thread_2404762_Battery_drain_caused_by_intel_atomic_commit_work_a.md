---
title: "Battery drain caused by intel_atomic_commit_work and intel_fbc_work_fn"
date: 2018-10-28
forum: Hardware
---

### Post by alessioalx on 2018-10-28
Hi all,

My laptop battery drains very quick (one hour).

Ubuntu 18.04.
Processor:  Intel® Core™ i7-7700HQ CPU @ 2.80GHz × 8
Graphics: Intel® HD Graphics 630 (Kaby Lake GT2)

I run Powertool and this is the output:

[TABLE="class: emphasis2, width: 95%"]
[TR="class: emph1"]
[TH="class: emph_title, align: left"]Usage[/TH]
[TH="class: emph_title, align: left"]Events/s[/TH]
[TH="class: emph_title, align: left"]Category[/TH]
[TH="class: emph_title, align: left"]Description[/TH]
[/TR]
[TR="class: emph1"]
[TD]7,3%[/TD]
[TD]0,06[/TD]
[TD]kWork[/TD]
[TD]intel_atomic_commit_work[/TD]
[/TR]
[TR="class: emph1"]
[TD]4,9%[/TD]
[TD]0,06[/TD]
[TD]kWork[/TD]
[TD]intel_fbc_work_fn[/TD]
[/TR]
[/TABLE]

Any idea?

---

### Post by TheFu on 2018-10-28
Have you ruled out a bad battery?

What does **acpi -V** show?
The top 2 lines will tell much.

Anything interesting in :
```
upower -i /org/freedesktop/UPower/devices/battery_BAT0
```

---

