---
title: "Epson V550 doesn't work anymore on Ubuntu 20.04"
date: 2020-11-03
forum: Hardware
---

### Post by poulou on 2020-11-03
Hi everybody,;my scanner Epson V550 doesn't work anymore since the recent installation of Ubuntu 20.04. I tried different solutions find on other forums but it still not working. I really don't know what to do. Any help would be appreciated.Many thanks in advance. Maybe this will help?

> poulou@poulou-K55VD:~$ sudo gedit /etc/udev/rules.d/55-epson-libsane.rules

(gedit:16568): Tepl-WARNING **: 20:01:47.782: GVfs metadata is not supported. Fallback to TeplMetadataManager. Either GVfs is not correctly installed or GVfs metadata are not supported on this platform. In the latter case, you should configure Tepl with --disable-gvfs-metadata.
poulou@poulou-K55VD:~$ scanimage -L


No scanners were identified. If you were expecting something different,
check that the scanner is plugged in, turned on and detected by the
sane-find-scanner tool (if appropriate). Please read the documentation
which came with this software (README, FAQ, manpages).
poulou@poulou-K55VD:~$ scanimage -L
device `epsonscan2:EPSON Scanner:esci2:usb:ES00EB:315' is a EPSON EPSON Scanner flatbed scanner




---

### Post by yapidumoac on 2020-11-04
[Linux Scanner Driver Download]("http://support.epson.net/linux/en/iscan.php?model=perfection-v550&version=1.0.0")

---

### Post by kurt18947 on 2020-11-04
As something of a last resort, there's always Vuescan.

---

