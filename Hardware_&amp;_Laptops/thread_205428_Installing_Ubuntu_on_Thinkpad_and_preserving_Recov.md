---
title: "Installing Ubuntu on Thinkpad and preserving Recovery partition"
date: 2006-06-28
forum: Hardware &amp; Laptops
---

### Post by gawron on 2006-06-28
The problem of installing Ubuntu on recent Thinkpad :-) (recent == a Thinkpad featuring Rapid Restore in a hidden partition, activated via Access IBM or ThinkVantage button press during boot) has been discussed before, but I have not found a good howto for Dapper Drake - so I decided to write a small one myself - see [here]("http://gawrysiak.org/corvus/?p=4"). It describes how to install Dapper on a Thinkpad T42, preserving both Windows XP and recovery functionality.

*Note that if you just go ahead and do standard Ubuntu install (via LiveCD) you will destroy your original MBR (which contains Rapid Restore bootloader). Above procedure alows you to preserve it **and ** install Linux*

---

