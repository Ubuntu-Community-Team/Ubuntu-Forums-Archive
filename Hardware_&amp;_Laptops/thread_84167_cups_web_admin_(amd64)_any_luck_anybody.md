---
title: "cups web admin (amd64) any luck anybody?"
date: 2005-10-30
forum: Hardware &amp; Laptops
---

### Post by metoo on 2005-10-30
I lost the connection to my usb laser printer brother hl-1430. It is attached via a mechanical switch, so I can share it among other local PCs, even if only one of them is running.
During my debian sid times it every here and then happend that I lost the printer and I could not print. Well, only from the amd64 machine this was. The i386 PC I have was always good.
Anyhow, as I use KDE, the KDE printer tools never brought the thing up again, only the deletion via the cups web admin page and a re-installation with that would enable printing. Bad but solvable.
Now with kubuntu I lost the printer again, but this time, I'm unable to access the web interface. Well, I can see the page but there is a message, that administration is not possible with it and that seems indeed to be the case. I searched the forum and it appears to be an old problem (it's not a bug, it's a feature!), but all given solutions would not work for me:
re-install, setting a cups password, messing in /etc/cups/cupsd.conf ...
So I wonder: Could anybody work around this limitation, preferably on amd64?
Mean while I could print the file on another machine attached to the usb-switch after transfering it there with an usb-stick. It has a partition with SuSE 10 on it... So the printer and the switch are fine (apparently, they worked before).
Help is appreciated.
(Why oh why are people making things so complicated?)

Update:
I can meanwhile connect to the web page:
Make sure, that the ServerName in /etc/cups/cupsd.conf is your host name (and not cupsy).
Unfortunately the problem still persists. Seems to be a usb naming problem, as the printer shows up OK in /proc/usb and lsusb and uses the right module usblp.
Somewhere in the system the /dev/usb/lp0 is transfered into something else usb//brother/... as the device name for /dev/usb/lp0 .
Well, after a restart I now have /dev/usb/lp0 back but I get this:
Unable to open USB device "usb:/dev/usb/lp0": Permission denied
To be continued...

Update 2, up and running again:
Madness! Solution: change the permission of /dev/lp0 and /dev/usb/lp0 to user/group = lp/lp (was root/lp).
No idea, what triggered the problem to appear...

---

