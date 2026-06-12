---
title: "xampp-control-panel.desktop installation error"
date: 2009-02-09
forum: Installation &amp; Upgrades
---

### Post by hoboy on 2009-02-09
i am trying to install xampp-control-panel.desktop,

luc@ubuntu:~$ gedit ~/.local/share/applications/xampp-control-panel.desktop
when I copy
[Desktop Entry]
Comment=Start/Stop XAMPP
Name=XAMPP Control Panel
Exec=gksudo "python /opt/lampp/share/xampp-control-panel/xampp-control-panel.py"
Icon[en_CA]=/usr/share/icons/Tango/scalable/devices/network-wired.svg
Encoding=UTF-8
Terminal=false
Name[en_CA]=XAMPP Control Panel
Comment[en_CA]=Start/Stop XAMPP
Type=Application
Icon=/usr/share/icons/Tango/scalable/devices/network-wired.svg

Then try to safe I get the following errors

Could not find the file /home/luc/.local/share/a…mpp-control-panel.desktop.

Please check that you typed the location correctly and try again.

---

### Post by hoboy on 2009-02-09
the problem is solved.
I have used
 sudo gedit /usr/share/applications/xampp-control-panel.desktop
 that is working like charme

---

