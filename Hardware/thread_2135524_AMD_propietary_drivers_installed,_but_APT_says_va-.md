---
title: "AMD propietary drivers installed, but APT says va-api needs fglrx + amd-cccle"
date: 2013-04-14
forum: Hardware
---

### Post by 1204 on 2013-04-14
Catalyst installed straight from the binary file and APT doesn't recognize when trying to install vdpau / va-api. Cannot make and install from DEB packages because caused problems. GPU is HD 4200 and OS Ubuntu 12.04 LTS.
```
sudo apt-get install xvba-va-driver libva-glx1 libva-x11-1 vainfo
```Then APT says it also needs fgrlx and amdcccle. Is there any way to avoid installing those two in this situation?

edit: Checked AMD site and there's new [Catalyst 13.1 for HD 4200]("http://support.amd.com/us/gpudownload/linux/legacy/Pages/legacy-radeon_linux.aspx"). I guess it will work when [making DEB]("http://wiki.cchtml.com/index.php/Ubuntu_Precise_Installation_Guide#Installing_Catalyst_Manually_.28from_AMD.2FATI.27s_site.29") packages, problem occurred with catalyst 12.9.

---

