---
title: "APP to Monitor Sensors ASUS Zenbook UX434FLC"
date: 2021-03-11
forum: Hardware
---

### Post by lordgallen on 2021-03-11
Unfortunately the BIOS has no information on CPU temp, chassis temp, fan speed, etc.... Is there a way to get a reading of theses sensors through either a Terminal command or an APP? Ubuntu 20.04 installed. Thank-You.

---

### Post by DuckHook on 2021-03-11
You may be interested in lm-sensors:```
duckhook@Zeus:~$  apt show lm-sensors
Package: lm-sensors
Version: 1:3.6.0-2ubuntu1
Priority: extra
Section: universe/utils
Origin: Ubuntu
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Original-Maintainer: Aurelien Jarno <aurel32@debian.org>
Bugs: https://bugs.launchpad.net/ubuntu/+filebug
Installed-Size: 406 kB
Depends: sed (>= 4.0.5-1), lsb-base (>= 3.2-13), libc6 (>= 2.4), libsensors5 (>= 1:3.5.0), perl:any
Suggests: fancontrol, read-edid, i2c-tools
Homepage: https://hwmon.wiki.kernel.org/lm_sensors
Task: xubuntu-desktop, ubuntustudio-desktop, ubuntukylin-desktop, ubuntu-budgie-desktop
Download-Size: 87.4 kB
APT-Manual-Installed: yes
APT-Sources: http://ca.archive.ubuntu.com/ubuntu focal/universe amd64 Packages
Description: utilities to read temperature/voltage/fan sensors
 Lm-sensors is a hardware health monitoring package for Linux. It allows you
 to access information from temperature, voltage, and fan speed sensors. It
 works with most newer systems.
 .
 This package contains programs to help you set up and read data from
 lm-sensors.

```
&#8230; and hddtemp:```
duckhook@Zeus:~$  apt show hddtemp
Package: hddtemp
Version: 0.3-beta15-53
Priority: extra
Section: universe/utils
Origin: Ubuntu
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Original-Maintainer: Aurelien Jarno <aurel32@debian.org>
Bugs: https://bugs.launchpad.net/ubuntu/+filebug
Installed-Size: 185 kB
Depends: libc6 (>= 2.15), debconf (>= 0.5) | debconf-2.0, lsb-base (>= 3.0-3)
Homepage: http://www.guzu.net/linux/hddtemp.php
Task: xubuntu-desktop, ubuntustudio-desktop, ubuntu-mate-core, ubuntu-mate-desktop, ubuntu-budgie-desktop
Download-Size: 47.7 kB
APT-Manual-Installed: no
APT-Sources: http://ca.archive.ubuntu.com/ubuntu focal/universe amd64 Packages
Description: hard drive temperature monitoring utility
 The hddtemp program monitors and reports the temperature of PATA, SATA
 or SCSI hard drives by reading Self-Monitoring Analysis and Reporting
 Technology (S.M.A.R.T.) information on drives that support this feature.
```
I try to keep my system as clean as possible, so I find these two are all I need. However, some like to then install *glances* or, if they want a drop down display on their tray, *psensor*. You can query their descriptions by using my earlier CLI examples as a guide.

---

### Post by lordgallen on 2021-03-12
Thank-You for that!, I will be taking a look.

---

