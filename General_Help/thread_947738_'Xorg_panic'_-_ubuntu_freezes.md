---
title: "'Xorg panic' - ubuntu freezes"
date: 2008-10-14
forum: General Help
---

### Post by inzaghi89 on 2008-10-14
Hi. I've got ubuntu 8.04.1, and it really like made for me system freezes. Only hard restart can help me (i mean: alt+sysrq+s,u,b - [...]+k don't work). This is my warning log (i think ;) ):
> @-pc:~$ grep -i error /var/log/syslog;grep -i fail syslog
Oct 14 17:52:57 -pc kernel: [ 15.768455] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
Oct 14 17:53:25 -pc NetworkManager: <WARN> nm_dbus_get_networks_cb(): error received: org.freedesktop.NetworkManagerInfo.NoNetworks - There are no wireless networks stored.. 
Oct 14 18:07:55 -pc kernel: [ 954.008768] end_request: I/O error, dev fd0, sector 0
Oct 14 18:07:55 -pc kernel: [ 954.008776] Buffer I/O error on device fd0, logical block 0
Oct 14 18:07:55 -pc kernel: [ 954.009257] end_request: I/O error, dev fd0, sector 0
Oct 14 18:07:55 -pc kernel: [ 954.009260] Buffer I/O error on device fd0, logical block 0
Oct 14 18:07:55 -pc kernel: [ 954.044774] end_request: I/O error, dev sr0, sector 0
Oct 14 18:07:55 -pc kernel: [ 954.044780] Buffer I/O error on device sr0, logical block 0
Oct 14 18:07:55 -pc kernel: [ 954.044787] Buffer I/O error on device sr0, logical block 1
Oct 14 18:07:55 -pc kernel: [ 954.044793] Buffer I/O error on device sr0, logical block 2
Oct 14 18:07:55 -pc kernel: [ 954.044797] Buffer I/O error on device sr0, logical block 3
Oct 14 18:07:55 -pc kernel: [ 954.044800] Buffer I/O error on device sr0, logical block 4
Oct 14 18:07:55 -pc kernel: [ 954.044804] Buffer I/O error on device sr0, logical block 5
Oct 14 18:07:55 -pc kernel: [ 954.044808] Buffer I/O error on device sr0, logical block 6
Oct 14 18:07:55 -pc kernel: [ 954.044811] Buffer I/O error on device sr0, logical block 7
Oct 14 18:07:55 -pc kernel: [ 954.047249] end_request: I/O error, dev sr0, sector 0
Oct 14 18:07:55 -pc kernel: [ 954.048324] end_request: I/O error, dev sr0, sector 4
Oct 14 18:08:12 -pc kernel: [ 971.410577] end_request: I/O error, dev fd0, sector 0
Oct 14 18:08:12 -pc kernel: [ 971.410587] Buffer I/O error on device fd0, logical block 0
Oct 14 18:08:12 -pc kernel: [ 971.411410] end_request: I/O error, dev fd0, sector 0
Oct 14 18:08:12 -pc kernel: [ 971.411413] Buffer I/O error on device fd0, logical block 0
Oct 14 18:08:12 -pc kernel: [ 971.424826] end_request: I/O error, dev sr0, sector 0
Oct 14 18:08:12 -pc kernel: [ 971.424831] Buffer I/O error on device sr0, logical block 0
Oct 14 18:08:12 -pc kernel: [ 971.426032] end_request: I/O error, dev sr0, sector 4
Oct 14 18:08:12 -pc kernel: [ 971.427404] end_request: I/O error, dev sr0, sector 0
Oct 14 18:08:12 -pc kernel: [ 971.429349] end_request: I/O error, dev sr0, sector 4
Oct 14 18:26:23 -pc kernel: [ 15.866326] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
Oct 14 18:26:52 -pc NetworkManager: <WARN> nm_dbus_get_networks_cb(): error received: org.freedesktop.NetworkManagerInfo.NoNetworks - There are no wireless networks stored.. 
grep: syslog: No such file or directory

How can i fix this problem? It's really clear version, because has only one day... So it's impossible to made something wrong and crash the system myself.

---

### Post by ram130 on 2008-10-14
are you running it from the live cd?

---

### Post by inzaghi89 on 2008-10-14
I've installed ubuntu from livecd, but it's installed version on hard drive.

---

### Post by inzaghi89 on 2008-10-15
So, could somebody help me? What should i do to fix that "feature"? ;)

---

### Post by inzaghi89 on 2008-10-15
New ones, from today:
> inzaghi89@inzaghi89-pc:~$ grep -i error /var/log/syslog;grep -i fail syslog
Oct 15 14:36:12 inzaghi89-pc kernel: [   33.178622] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
Oct 15 14:36:40 inzaghi89-pc NetworkManager: <WARN>  nm_dbus_get_networks_cb(): error received: org.freedesktop.NetworkManagerInfo.NoNetworks - There are no wireless networks stored.. 
Oct 15 17:58:00 inzaghi89-pc kernel: [   16.088761] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
Oct 15 17:58:29 inzaghi89-pc NetworkManager: <WARN>  nm_dbus_get_networks_cb(): error received: org.freedesktop.NetworkManagerInfo.NoNetworks - There are no wireless networks stored.. 
Oct 15 22:31:43 inzaghi89-pc kernel: [   15.374822] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
Oct 15 22:32:13 inzaghi89-pc NetworkManager: <WARN>  nm_dbus_get_networks_cb(): error received: org.freedesktop.NetworkManagerInfo.NoNetworks - There are no wireless networks stored.. 
grep: syslog: No such file or directory


---

### Post by BeigeGenius on 2009-02-02
hmm interesting it is I get this just before a freeze as well "NetworkManager: <WARN>  nm_dbus_get_networks_cb(): error received: org.freedesktop.NetworkManagerInfo.NoNetworks - There are no wireless networks stored.. " 
This looks like a nice bug in networkmanager!

---

### Post by lautarop on 2009-08-02
bump?

---

