---
title: "apport terminal logs: where are they?"
date: 2009-05-06
forum: Installation &amp; Upgrades
---

### Post by superbiskit on 2009-05-06
I see that, when _apport_ uploads a bug report about a package that failed to install/upgrade, there is a log of the installation session labeled [FONT="Courier New"]DpkgTerminalLog.txt[/FONT] attached.
I have not been able to find such a file on my machine after a run, and there have been numerous times I've wanted a log of an _aptitude_ run (for example).  I have been trying [FONT="Courier New"]aptitude >log[/FONT], but if there's an automagic way to capture the information, that would be better.

TIA

---

### Post by Partyboi2 on 2009-05-06
Have a look at /var/log/aptitude or /var/log/apt/term.log

---

