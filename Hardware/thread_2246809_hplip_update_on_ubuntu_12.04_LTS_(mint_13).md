---
title: "hplip update on ubuntu 12.04 LTS (mint 13)"
date: 2014-10-03
forum: Hardware
---

### Post by Romualdou on 2014-10-03
Hello,

I had problems getting a HP Deskjet 1510 properly working on Mint 13 (Ubuntu 12.04) LTS and finally figured out that the installed version of hplip (3.12.2) has no support for this printer. Minumum hplip version required is 3.13.8 (see [http://hplipopensource.com/hplip-web/models/deskjet_aio/deskjet_1510_series.html](http://hplipopensource.com/hplip-web/models/deskjet_aio/deskjet_1510_series.html))
Upgrading hplip to the latest version solved the problem. 

**My question:** why is there no current hplip version available from synaptics, although 12.04 is LTS with support until 2017?

Regards

---

### Post by Vladlenin5000 on 2014-10-03
Because only kernel, security issues and some other software gets updates. Everything else is frozen for that version.

---

### Post by grahammechanical on 2014-10-03
Linux Mint might be built on Ubuntu 12.04 but it should not be viewed as Ubuntu 12.04. Those of us using Ubuntu 12.04 would now be running 12.04.5 and that included a new hardware enablement stack and it may have included updated drivers for printers. I do not really know. Nor do I know if the Linux Mint developers pass on the work the Ubuntu developers do in keeping 12.04 up to date with progress made by the Linux developers.

---

### Post by Romualdou on 2014-10-05
Thanks for the replies. 

So according to Vladlenin, no update other than kernel and security. According to Grahammechanical not so sure, maybe also hplip update with 12.04.5. And also maybe some differences between mint and ubuntu. I'll post the same discussion in mint forums. 

In the meantime I checked on Mint 17 (based on Ubuntu 14.04 LTS), hplip is up to date (3.14.3) 

It would be interesting if somebody running Ubuntu 12.04.5 could post the current version of hplip it comes with. 

The issue I have here is having Linux running on the PCs from some older and geographicaly distant relatives and stability as well as nothing changing is very important for these users. So LTS version are great. But if simple things like installing a new printer stop working out of the box on LTS version after a while because only some system aspects are updated, it starts getting complicated. 

Regards,

---

### Post by Romualdou on 2014-10-05
Follow-up:
I browsed the packages under [http://packages.ubuntu.com/precise-updates/allpackages](http://packages.ubuntu.com/precise-updates/allpackages)
Apparently, hplip ist not updated there:
[hplip]("http://packages.ubuntu.com/precise-updates/hplip") (3.12.2-1ubuntu3.4)
HP Linux Printing and Imaging System (HPLIP)

So the issue would be the same with ubuntu 12.04.5 LTS as under mint if I'm right.

---

