---
title: "ACPI - cooling_mode always in critical"
date: 2005-12-02
forum: Hardware &amp; Laptops
---

### Post by pear-i on 2005-12-02
hey there i'm on a Dell C640 Laptop, but, ever since i upgraded to breezy, my laptop has started to get really loud and noisy -- whereas previously on warty it was ok -- was silent like most laptops -- when i was scaling on 1.2 ghz instead of the max 2.0 ghz

however now even on default at 1.2 --

when i cat  /proc/acpi/thermal_zone/THM/cooling_mode it always returns critical despite my temperature being low like at 43 or something

i've cat the trippoints and that says 99 -- not sure if this is a bug or misconfiguration.... anyone have any ideas how to fix this?

---

