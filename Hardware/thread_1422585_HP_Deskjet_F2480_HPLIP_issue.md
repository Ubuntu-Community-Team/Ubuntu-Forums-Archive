---
title: "HP Deskjet F2480 HPLIP issue"
date: 2010-03-05
forum: Hardware
---

### Post by Bl&#259;noz on 2010-03-05
Using: Jaunty 9.04 (x32)
Printer: HP Deskjet F2480
Driver: [http://hplipopensource.com/hplip-web/index.html](http://hplipopensource.com/hplip-web/index.html) -> hplip-3.10.2
- After installation, running **hp-check** in terminal and resolving needed dependecies in Synaptic. Output: [http://desen.pastebin.com/Jst2Rd9v](http://desen.pastebin.com/Jst2Rd9v) . Ignore error on line 255, it was eliminated after reinstalling hplip-3.10.2 but i cannot get rid of errors on lines 103 and 242.

# So, i'm deleting the printer from "Printers", restarting system, i'm plugging in the printer and it gets automatically detected and installed (proper ppd for F2400 series). While i'm trying to print a test page, i receive this error -> [http://img715.imageshack.us/img715/9666 … rerror.png]("http://img715.imageshack.us/img715/9666/foomaticripfiltererror.png")

Additionally im getting "cups-missing-filter" error in Printer Configuration -> Ink/tonner levels.

hplip-3.10.2.run - has been installed 1. manually (deleted) and 2. automated, by running the .run script. Ofc, nothing worked.

Any help would be very appreciated, i really need this printer up and running, so i must not run a dual-boot.

Cheers.

---

