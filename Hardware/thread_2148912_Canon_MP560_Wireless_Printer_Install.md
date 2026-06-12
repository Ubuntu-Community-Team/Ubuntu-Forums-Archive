---
title: "Canon MP560 Wireless Printer Install"
date: 2013-05-27
forum: Hardware
---

### Post by Windsor62 on 2013-05-27
Hi all, just installed Lubuntu 13.04. Having a problem adding the printer in as much as the +ADD button located within PRINTERS-LOCALHOST box is greyed out!  :( Only the CONNECT button is operational?  I've already loaded the Canon MP560 drivers ready to install printer.

Thanks!

---

### Post by pdc on 2013-05-27
[http://askubuntu.com/questions/112927/add-new-printer-disabled-grayed-out-using-gnome-shell](http://askubuntu.com/questions/112927/add-new-printer-disabled-grayed-out-using-gnome-shell)

this thread suggests you add a new printer by loading this link into a spare browser window

[http://localhost:631/admin](http://localhost:631/admin)

click on the left button "Add new printer" .......a permission dialogue will appear ...............

from memory, the username is [COLOR="#0000FF"]root[/COLOR] and the password is your sudo password

________________________________________________________________________________________________

>  [COLOR="#800080"]I've already loaded the Canon MP560 drivers ready to install printer.[/COLOR]

.......so which ones are they please; and are you using 32bit lubuntu?

---

### Post by Windsor62 on 2013-05-28
Installed cnifilter-mp560series-3.20-1-i386-deb.tar.gz from Canon Asia web site. I'm using Lubuntu 13.04 32bit on a 4 year old Medion laptop with 3Gb RAM.

---

### Post by pdc on 2013-05-28
that all sounds good; you can check the drivers with the command

> sudo dpkg -l | grep cnijfilter

.......that should show the common driver and the MP560 driver

> system-config-printer

is another way to open a dialogue box: perhaps LXDE limits things a little

---

