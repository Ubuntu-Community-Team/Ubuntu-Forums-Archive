---
title: "Canon DR-2580C scanner on U 10.04"
date: 2010-08-11
forum: Hardware
---

### Post by potestas on 2010-08-11
I have a Canon DR-2580C document scanner that represents the last piece of hardware tying me to Microsoft.  The scanner has not worked in any Ubuntu release until 10.04.  I tried simple scan and it would at least pull a page through the scanner but pretty poor results.  Scanning through XSane Image Scanner fails every time (illegal argument).

Anyone out there know of a way to get this scanner working?  Please bear in mind, I'm not a developer but pretty comfortable at the command line.

---

### Post by IcarusR on 2010-08-11
You may be able to get sane to work by defining your scanner in the config file. Read the backend man page for details...

[http://www.sane-project.org/man/sane-canon_dr.5.html]("http://www.sane-project.org/man/sane-canon_dr.5.html")

---

