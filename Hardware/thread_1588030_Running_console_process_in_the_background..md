---
title: "Running console process in the background."
date: 2010-10-04
forum: Hardware
---

### Post by matusroman on 2010-10-04
When I go to konsole  CTRL+ALT+F1 ..... F6 there is still run that :

Procedures from konsole:
(this still running and display is flashing every cca 45 min.)
Sep 29 22:12:08 ubuntu-mrn kernel: [ 3584.324430] radeon 0000:01:05.0: HDMI Type A-1: EDID block 0 invalid.
Sep 29 22:12:18 ubuntu-mrn kernel: [ 3594.400774] 
Sep 29 22:12:18 ubuntu-mrn kernel: [ 3594.455106] 
Sep 29 22:12:18 ubuntu-mrn kernel: [ 3594.508366] 
Sep 29 22:12:19 ubuntu-mrn kernel: [ 3594.562315] 
Sep 29 22:12:19 ubuntu-mrn kernel: [ 3594.562319] radeon 0000:01:05.0: HDMI Type A-1: EDID block 0 invalid.
Sep 29 22:12:29 ubuntu-mrn kernel: [ 3604.639242] 
Sep 29 22:12:39 ubuntu-mrn kernel: [ 3614.708027] 
Sep 29 22:12:39 ubuntu-mrn kernel: [ 3614.761870] 
Sep 29 22:12:39 ubuntu-mrn kernel: [ 3614.816912] 
Sep 29 22:12:39 ubuntu-mrn kernel: [ 3614.869768] 
Sep 29 22:12:39 ubuntu-mrn kernel: [ 3614.869772] radeon 0000:01:05.0: HDMI Type A-1: EDID block 0 invalid.
Sep 29 22:12:49 ubuntu-mrn kernel: [ 3624.940715] 
Sep 29 22:12:49 ubuntu-mrn kernel: [ 3625.000506] 
Sep 29 22:12:49 ubuntu-mrn kernel: [ 3625.056629] 
Sep 29 22:12:49 ubuntu-mrn kernel: [ 3625.117293] 
Sep 29 22:12:49 ubuntu-mrn kernel: [ 3625.117297] radeon 0000:01:05.0: HDMI Type A-1: EDID block 0 invalid.
Sep 29 22:12:59 ubuntu-mrn kernel: [ 3635.188560] 
Sep 29 22:12:59 ubuntu-mrn kernel: [ 3635.249480] 
Sep 29 22:12:59 ubuntu-mrn kernel: [ 3635.311205] 
Sep 29 22:12:59 ubuntu-mrn kernel: [ 3635.368655] 
Sep 29 22:12:59 ubuntu-mrn kernel: [ 3635.368659] radeon 0000:01:05.0: HDMI Type A-1: EDID block 0 invalid.
Sep 29 22:13:09 ubuntu-mrn kernel: [ 3645.451944] 
Sep 29 22:13:09 ubuntu-mrn kernel: [ 3645.515674] 
Sep 29 22:13:10 ubuntu-mrn kernel: [ 3645.579831] 
Sep 29 22:13:10 ubuntu-mrn kernel: [ 3645.635591] 
Sep 29 22:13:10 ubuntu-mrn kernel: [ 3645.635595] radeon 0000:01:05.0: HDMI 

Problem is extern monitor resolution is regulary damaged by this procedure on backround and is regulary flashing. Any idea how stop this procedures on backround ?

Ubuntu 10.10 Maverick  Meerkat on
Toshina Equium A300D - 13x AMD Turion64 extern monitor Acer x223w 22"

---

### Post by psusi on 2010-10-04
That is the kernel complaining, not a console process.  Did you install the proprietary video drivers?

---

### Post by matusroman on 2010-10-04
> **psusi said:**
> That is the kernel complaining, not a console process.  Did you install the proprietary video drivers?

Video  working only on mesa, if I have install fglrx something is not corect because fglrxinfo answer is faut. :confused:

---

