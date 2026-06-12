---
title: "Permissions problem with USB scanner"
date: 2008-04-17
forum: Hardware &amp; Laptops
---

### Post by killerclick on 2008-04-17
$ sane-find-scanner

found USB scanner (vendor=0x03f0 [hewlett packard], product=0x2605 [hp scanjet], chip=RTS8822L-01H) at libusb:002:003


$ scanimage -L

No scanners were identified. If you were expecting something different,
check that the scanner is plugged in, turned on and detected by the
sane-find-scanner tool (if appropriate). Please read the documentation
which came with this software (README, FAQ, manpages).


$ sudo scanimage -L

device `hp3900:libusb:002:003' is a Hewlett-Packard Scanjet 3800 flatbed scanner



I've added the following to /etc/udev/rules.d/45-libsane.rules:
# Hewlett-Packard ScanJet 3800
SYSFS{idVendor}=="03f0", SYSFS{idProduct}=="2605", MODE="664", GROUP="scanner"

Still scanimage -L reports no scanners found and so does XSane!



$ groups killerclick
killerclick : killerclick adm dialout cdrom floppy audio dip video plugdev scanner lpadmin admin netdev powerdev




So this is a problem with USB permissions, right? How do I solve this? Please bear in mind that I'm a newbie...

---

### Post by killerclick on 2008-04-17
Solved... don`t know what the problem was (the scanner was accessible only as root) but the solution was to instal Sane backend 1.0.19 for Hardy, had to install something called lib6 or libc whatever and now the scanner is working properly......... not thanks to any of you,

I`m never recommending Linux to anyone anymore. Community support sucks (except when defending Linux and bashing Windows) and I spent more than 12 hours getting Ubuntu to work properly. By my price list that`s just enough for a nice new copy of Windows XP... and this is just the first two weeks.

---

### Post by nge on 2008-04-18
> Community support sucks

Don't speak like that so easily. Usually it takes 1-2 or even more bumps to make your post even recognized in such a large forum with such amount of threads created per minute..

---

