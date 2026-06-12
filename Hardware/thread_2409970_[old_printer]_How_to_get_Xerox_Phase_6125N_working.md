---
title: "[old printer] How to get Xerox Phase 6125N working on Ubuntu?"
date: 2019-01-09
forum: Hardware
---

### Post by 3jl on 2019-01-09
Hi all,
I have recently installed my first Ubuntu server (virtualised using ESXi) and am now trying to connect an old laserjet printer (Xerox Phaser 6125N). CUPS comes with a driver for Phaser 6130, but this one fails (printer is detected, there is a connection, but printing jobs are cancelled).

I have found suggestions on this and other forums: [https://ubuntuforums.org/showthread.php?t=1552166](https://ubuntuforums.org/showthread.php?t=1552166)

But the files referenced to are no longer there... What would be the best way to go about this? Is it possible to get this old beast running in the first place?

Version: Ubuntu 18.04.1 LTS on 64bit Intel (Xeon E3-1245v6)

Thanks! J

---

### Post by 3jl on 2019-01-22
[COLOR=#000000][FONT=Roboto]Found it:[URL="https://rickvanderzwet.nl/trac/personal/wiki/XeroxPhaser6125N"]

https://rickvanderzwet.nl/trac/personal/wiki/XeroxPhaser6125N[/URL][/FONT][/COLOR]
[COLOR=#000000][FONT=Roboto](I was a bit reluctant as it is not an official distribution...)[/FONT][/COLOR]
[COLOR=#000000][FONT=Roboto]sudo dpkg -i cups-xerox-phaser-6125n-1.0.0.deb[/FONT][/COLOR]
[COLOR=#000000][FONT=Roboto]sudo apt-get install libc6-i386[/FONT][/COLOR]
[COLOR=#000000][FONT=Roboto]sudo apt-get install libcups2:i386

[/FONT][/COLOR]

---

