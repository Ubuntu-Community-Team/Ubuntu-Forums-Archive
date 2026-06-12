---
title: "Installing printer"
date: 2010-01-31
forum: Hardware
---

### Post by Eddie Parker on 2010-01-31
I am running Ubuntu 9.10.I tried to install a brother fax 2850 lpr printer.I downloaded the driver from the Brother website. The trouble is that I am now unable to open Synaptic package manager. The messages I get are: "E: The package fax2850lpr needs to be reinstalled, but I can't find an archive for it.
E: Internal error opening cache (1). Please report." and "an error occurred, please run Package Manager from the right click menu or apt-get in a terminal to see what is wrong. The error message was"unknown error <type exceptions. System error" The package fax2850lpr needs to be reinstalled but I can't find an archive for it. This usually means that your installed packages have unmet dependencies"
How do I remove it, reinstall synaptic, install the printer please .All the above suggestions failed.

---

### Post by IcarusR on 2010-02-01
I would try uninstalling the brother package you installed.

From a terminal...

```
sudo apt-get purge package name
```

---

### Post by malibusurfer2 on 2010-03-12
On Ubuntu Jaunty 9.04 have Epson NX-415 3 in one printer working well sing CUPS, but every time I turn it on, Ubuntu thinks it is a new printer and wants to search for a driver and ad it as another printer. I cancel the little windows it opens and go about my printing or scanning, but it is annoying. Any ideas?

---

