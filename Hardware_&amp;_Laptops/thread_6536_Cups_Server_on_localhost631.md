---
title: "Cups Server on localhost:631"
date: 2004-11-29
forum: Hardware &amp; Laptops
---

### Post by thom on 2004-11-29
I'd like to configure my printer via localhost:631 because I have some problems using gnome-cups-manager. But the Cups Web Interface says "Administrative tasks have been disabled for security reasons. Please use Menu Computer > System configuration > Printing.". How can I reenable administrative tasks?

Thanks,
thom

---

### Post by thom on 2004-11-29
I found the solution: Just RTFM ;).

/usr/share/doc/cupsys/README.debian.gz explains how to reenable the web interface:

> Administration over the web interface is disabled by default since it
requires the CUPS daemon to be able to read /etc/shadow.  If you want to
enable web administration with shadow passwords (authentication type
'basic'), put the user cupsys into group shadow by

  adduser cupsys shadow

as root.

---

### Post by electroglas on 2004-12-01
This fixed me right up!

Printing needs major work on Hoary. I had to add cupsys to the group "shadow" to use the web interface (since the printer configuration sucks), endure printer configuration crashes, download hpijs, set the  printer port to PTAL mlc: par (WTF) and set the default paper size to letter instead of A-4 in /etc/papersize. I'm sure I have overlooked a few steps in this myriad of modifications. 

Hopefully, this will all be simplified as development continues on Hoary.

---

### Post by mahalram on 2004-12-15
[QUOTE=thom]I found the solution: Just RTFM ;).

/usr/share/doc/cupsys/README.debian.gz explains how to reenable the web interface:[/QUOTE]

Unfortunately this didnt work for me. When I click on administration in the web interface I get a username password prompt dialog. But when I supply it (root and rootpasswd) the same dialog comes back again :(

I dis do adduser cupsys shadow,,,,

---

### Post by mahalram on 2004-12-15
[QUOTE=mahalram]Unfortunately this didnt work for me. When I click on administration in the web interface I get a username password prompt dialog. But when I supply it (root and rootpasswd) the same dialog comes back again :(

I dis do adduser cupsys shadow,,,,[/QUOTE]

Nevermind...
Just had to reboot :(

probably restaring cups would have done the trick too ...

---

