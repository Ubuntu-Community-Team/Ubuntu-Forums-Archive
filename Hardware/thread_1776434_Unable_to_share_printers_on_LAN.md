---
title: "Unable to share printers on LAN"
date: 2011-06-06
forum: Hardware
---

### Post by taxidimu on 2011-06-06
Ubuntu 10 Server, Samba, Windows clients.
Sharing files with W clients works fine.
Now I have installed a couple of printers on Ubuntu (Epson Stylus and Canon Pixma).
I can either print form this server, and administer them via [http://myserver:631](http://myserver:631) (either from the server and from clients).
But I cannot browse and then print form clients.

At boot error_log gives[INDENT][COLOR=Navy]W [31/May/2011:12:04:43 +0200] Duplicate listen address "/var/run/cups/cups.sock" ignored![/COLOR]
[COLOR=Navy]E [31/May/2011:12:04:43 +0200] Unable to bind socket for address ::1:631 - Address already in use.[/COLOR]
[COLOR=Navy]E [31/May/2011:12:04:43 +0200] Unable to bind socket for address 127.0.0.1:631 - Address already in use.[/COLOR]
[/INDENT][COLOR=Black]from smb.conf[/COLOR][INDENT][COLOR=Navy]########## Printing ##########

# If you want to automatically load your printer list rather
# than setting them up individually then you'll need this
; mysetting...
#   load printers = yes
   load printers = yes
; ... end

# lpr(ng) printing. You may wish to override the location of the
# printcap file
;   printing = bsd
;   printcap name = /etc/printcap

# CUPS printing.  See also the cupsaddsmb(manpage in the
# cupsys-client package.
;   printing = cups
;   printcap name = cups
[/COLOR][/INDENT]Here attached: cupsd.conf, printers.conf

Thank you for help!

---

