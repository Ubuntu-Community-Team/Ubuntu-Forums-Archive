---
title: "Kubuntu: Problems after kernel upgrade:2.6.24-19 to 2.6.24-23"
date: 2009-01-12
forum: Installation &amp; Upgrades
---

### Post by Vaethe on 2009-01-12
I have been running Kubuntu 8.04.1 on kernel 2.6.24-19 for sometime now, and recently ran the Adept Package Manager to update the system. Adept downloaded and installed a new kernel (2.6.24-23).

After installation of the 2.6.24-23 Kernel, I now have no GUI at all. After displaying the Kubuntu splash screen while loading, Kubuntu boots to a text-based login prompt. After logging in via the text-based login prompt, I am presented only with a command prompt.

Running "startx" or "sudo startx" at the command prompt results in an error the ends with: 

Fatal server error: no screens found
giving up
xinit: Connection reset by peer (errno 104): unable to connect to X server
xinit: No such process (errno 3): Server error
xauth: error in locking authority file /home/brendan/.Xauthority

I am at the moment booting back off the 2.6.24-19 kernel, but would like to see if there's some fix for this error.

Thanks in advance,
Brendan

---

### Post by Vaethe on 2009-01-12
Fixed:

Downloaded a new graphics driver from NVIDIA, which built and installed a new kernel interface.

---

### Post by Egi_Power on 2009-01-12
If you fixed it, you could mark the thread as SOLVED @ the top of the page: Thread Tools.

---

