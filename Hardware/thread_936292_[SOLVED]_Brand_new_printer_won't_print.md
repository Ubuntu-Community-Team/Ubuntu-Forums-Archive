---
title: "[SOLVED] Brand new printer won't print"
date: 2008-10-02
forum: Hardware
---

### Post by absolutezero1287 on 2008-10-02
I recently bought an HP F4280 and I upgraded hplip to the latest version.
My printer was recognized but whenever I request a print job it says that it has been completed. However, my printer doesn't actually print anything.
Here is the output of hp-check. Please help. 
[http://ubuntu.pastebin.com/f2327f382](http://ubuntu.pastebin.com/f2327f382)

---

### Post by absolutezero1287 on 2008-10-06
BUMP someone please help

---

### Post by phidia on 2008-10-06
Among the many errors in the output you linked is this: > #
warning: Printer is not HPLIP installed. Printers must use the hp: or hpfax: CUPS backend to function in HPLIP.

Install hplip-gui and install the device using that interface.

---

### Post by absolutezero1287 on 2008-10-06
I installed it via the CUPS web interface and was able to print a test page.I was also able to print a pdf of a lecture on Single Variable Calculus from MIT's OpenCourseWare site.
[http://ocw.mit.edu]("http://ocw.mit.edu")
I guess that it's safe to say that it's installed.
Thank you very much for all your help.

One more question: I have the HP status device and HP device manager installed. The device manager doesn't detect the printer. Is it safe to remove it?

---

### Post by absolutezero1287 on 2008-10-06
Solved. Uninstalled HP toolbox and it still prints without a hitch.

---

