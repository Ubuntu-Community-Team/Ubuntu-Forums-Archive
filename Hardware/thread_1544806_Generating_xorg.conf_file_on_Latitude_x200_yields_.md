---
title: "Generating xorg.conf file on Latitude x200 yields bad things"
date: 2010-08-03
forum: Hardware
---

### Post by ArconsII on 2010-08-03
I'm trying to generate an xorg.conf file so I can do some manual configuration on a latitude x200 using Xorg -configure. When booting from the new xorg.conf file, however, the GUI refuses to initialize and the boot just hangs at the Xubuntu flash screen. Deleting the file causes it to boot fine. What could be the problem?

---

### Post by anglican on 2010-08-04
> **ArconsII said:**
> I'm trying to generate an xorg.conf file so I can do some manual configuration on a latitude x200 using Xorg -configure. When booting from the new xorg.conf file, however, the GUI refuses to initialize and the boot just hangs at the Xubuntu flash screen. Deleting the file causes it to boot fine. What could be the problem?
If you boot into recovery mode, login, then try ```
"sudo service gdm start"
``` you may get some idea of where the problem is. In particular you will be able to examine /var/log/Xorg.0.log to see what errors are preventing Xorg from starting.

H

---

