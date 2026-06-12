---
title: "HP LaserJet Pro 1102w not printing (but test page!)"
date: 2010-08-30
forum: Hardware
---

### Post by coslo on 2010-08-30
Hello, I am encountering some issues with an HP laserjet 1102w printer (running on a HP DV3 laptop with Ubuntu 9.10). Drivers for this printer are not available directly in 9.10, but after installing the latest version of hplip (v3.10.6) and creating a new printer for the laserjet, I could eventually print test pages from the CUPS webpage or from Administration > Printing. Now, the problem is that printing files from terminal (or anywhere else) doesn't work: error is ```
/usr/lib/cups/filter/foomatic-rip failed
``` What am I doing wrong? I checked with the hp-check tool and the hplip installation seems sane (I could post the output if needed). I found few possible solutions to similar issues here

[http://hplipopensource.com/node/337](http://hplipopensource.com/node/337)
[http://foo2zjs.rkkda.com/](http://foo2zjs.rkkda.com/)

but before uninstalling and installing things all over again, I wanted to ask your advice. In particular, what is puzzling to me is that I can print the test page only, nothing more. Am I missing something very basic? Any help/suggestions?

---

### Post by coslo on 2010-08-31
Bump. Any help?

---

### Post by coslo on 2010-08-31
OK! It seems like the indications of the first link solved the problem. I reinstalled hplip with different configure flags and now it works fine.

---

