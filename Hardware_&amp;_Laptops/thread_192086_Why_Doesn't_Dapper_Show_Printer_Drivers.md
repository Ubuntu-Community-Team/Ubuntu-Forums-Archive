---
title: "Why Doesn't Dapper Show Printer Drivers?"
date: 2006-06-08
forum: Hardware &amp; Laptops
---

### Post by lakelovers on 2006-06-08
A number of posts ask about vacant print drivers in Dapper but nobody seems to have an answer. I have a Canon i560 printer running on Turboprint, which I cannot get Dapper to recognize. The Driver option in Cups is empty.  Need help.

**Edit** Well I answered my own question. I got an update notice which included a Cups file, so now my printer and Turbopint are recognized in the Driver window of Cups. However, my printer still will not print. I get the error message that the print server is not accepting jobs. Can't figure out why. Any suggestioins?

---

### Post by razahel on 2006-06-08
Hi,

is your user member of lp and lpadmin?
try adding your printer as super user with the interfaceof turborprint xtpsetup
Hope it helps.
If so try printing 4 pages on one sheet and be so kind to  tell me if the printer does what you want.


regards razahel

---

### Post by lakelovers on 2006-06-08
[QUOTE=razahel]Hi,

is your user member of lp and lpadmin?
try adding your printer as super user with the interfaceof turborprint xtpsetup
Hope it helps.
If so try printing 4 pages on one sheet and be so kind to  tell me if the printer does what you want.
regards razahel[/QUOTE]

I set up the printer as super user with xtpsetup. Still no printing function. When I try a test print, I get: "Printing to 'tp0' failed with error code: 1286
is the printer paused?" The printer is not paused and is "ready."

---

### Post by Turin Turambar on 2006-06-08
You must use the latest Turboprint driver - 1.94-3 that is. As you probably noticed, I had the same problem - Canon i350 just wouldn't print. I fixed it with 1.94-3.

---

