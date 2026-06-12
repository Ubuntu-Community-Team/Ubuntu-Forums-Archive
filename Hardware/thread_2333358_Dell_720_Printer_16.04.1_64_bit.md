---
title: "Dell 720 Printer 16.04.1 64 bit"
date: 2016-08-09
forum: Hardware
---

### Post by giulio-canevari on 2016-08-09
I'm posting this since the howto is quite outdated. The printer still works with 16.04.1 64 bit.

I have tried many things so i don't know if this list is 100% ok but i think is better than nothing ;) . No i don't have anymore the printer i've installed it for a friend.

1) Install 32 bit libstdc++ and libcupsimage2

$ sudo dpkg --add-architecture i386

$ sudo apt-get update

$ sudo apt-get install libstdc++5:i386  libcupsimage2:i386

2) Download and install (e.g. with gdebi) the [lexmark.z600-0.4.deb]("https://help.ubuntu.com/community/HardwareSupportComponentsPrinters/LexmarkPrinters?action=AttachFile&do=view&target=lexmark.z600-0.4.deb") package.

Then open the printer tool (depends on ubuntu version) and add the printer (choose lexmark z600).

Should work ;) .

(if it doesn't, find and create a symlink to z600 and to rastertoz600 in /usr/local/bin )

Hope this could be useful.

---

