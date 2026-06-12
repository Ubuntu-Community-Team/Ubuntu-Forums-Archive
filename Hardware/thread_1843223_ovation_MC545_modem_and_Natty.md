---
title: "ovation MC545 modem and Natty"
date: 2011-09-13
forum: Hardware
---

### Post by Pontus12 on 2011-09-13
Please, excuse my poor english!
Does anyone know, how to get Novatel's ovation MC545 dual carrier modem to work in Natty or coming Oneiric. The modem can reach about 41 Mgb in 4G network, which is coming at the end of this year in Finland, and it reaches 21 Mgb in 3G.  I need a fast modem in our telephone network Huawei E358 I think works also, but I have not found it in our Ubuntu forum.
Novatek gives instruction in [http://www.novatelwireless.com/index.php?option=com_content&view=article&id=278:support-by-host-platform&catid=33:technical-support](http://www.novatelwireless.com/index.php?option=com_content&view=article&id=278:support-by-host-platform&catid=33:technical-support)
It did not work Ubuntu say's that the package is weak and recomends not to install. I installed anyway, but I got folowing errors:
Lintian check results for /home/jotaarkka/Lataukset/novatel_modem_drivers_config_1.1_6.deb:
E: novatel-modem-drivers-config: wrong-file-owner-uid-or-gid etc/ 1000/1000
E: novatel-modem-drivers-config: wrong-file-owner-uid-or-gid etc/hal/ 1000/1000
E: novatel-modem-drivers-config: wrong-file-owner-uid-or-gid etc/hal/fdi/ 1000/1000
E: novatel-modem-drivers-config: wrong-file-owner-uid-or-gid etc/hal/fdi/information/ 1000/1000
E: novatel-modem-drivers-config: wrong-file-owner-uid-or-gid etc/hal/fdi/information/11-nvtl-modem.fdi 1000/1000
E: novatel-modem-drivers-config: wrong-file-owner-uid-or-gid etc/hal/fdi/information/11-nvtl-modem.fdi~ 1000/1000
E: novatel-modem-drivers-config: wrong-file-owner-uid-or-gid etc/udev/ 1000/1000
E: novatel-modem-drivers-config: wrong-file-owner-uid-or-gid etc/udev/nvtl_modem.sh 1000/1000
E: novatel-modem-drivers-config: wrong-file-owner-uid-or-gid etc/udev/rules.d/ 1000/1000
E: novatel-modem-drivers-config: wrong-file-owner-uid-or-gid etc/udev/rules.d/nvtl_modem.rules 1000/1000
E: novatel-modem-drivers-config: wrong-file-owner-uid-or-gid usr/ 1000/1000
E: novatel-modem-drivers-config: wrong-file-owner-uid-or-gid usr/share/ 1000/1000
E: novatel-modem-drivers-config: wrong-file-owner-uid-or-gid usr/share/doc/ 1000/1000
E: novatel-modem-drivers-config: wrong-file-owner-uid-or-gid usr/share/doc/novatel_modem_drivers/ 1000/1000
E: novatel-modem-drivers-config: wrong-file-owner-uid-or-gid usr/share/doc/novatel_modem_drivers/copyright 1000/1000
E: novatel-modem-drivers-config: wrong-file-owner-uid-or-gid usr/share/doc/novatel_modem_drivers/hardwarelist 1000/1000

If somebody could help, I would be very obliged.

---

