---
title: "problem with Zimbra Desktop"
date: 2008-08-11
forum: General Help
---

### Post by tone77 on 2008-08-11
Thanks to the weekly newsletter I saw that Zimbra Desktop was now apart of the partner repository.  So I tried to install and got a lovely error.  Any suggestions would be greatly appreciated.

> sudo aptitude install zdesktop
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      
The following NEW packages will be installed:
  zdesktop 
0 packages upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/51.5MB of archives. After unpacking 51.4MB will be used.
Writing extended state information... Done
Selecting previously deselected package zdesktop.
(Reading database ... 169423 files and directories currently installed.)
Unpacking zdesktop (from .../zdesktop_0.90.1249beta-hardy1_i386.deb) ...
Setting up zdesktop (0.90.1249beta-hardy1) ...

** (x-www-browser:15568): WARNING **: Unable to connect to session bus: Failed to connect to socket /tmp/dbus-KWTyZyNbnH: Connection refused
dpkg: error processing zdesktop (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 zdesktop
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Setting up zdesktop (0.90.1249beta-hardy1) ...

** (x-www-browser:15623): WARNING **: Unable to connect to session bus: Failed to connect to socket /tmp/dbus-mnbjRKslBO: Connection refused
dpkg: error processing zdesktop (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 zdesktop
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Writing extended state information... Done
Building tag database... Done

Firefox is set as my default browser under System -> Preferences -> Preferred Applications

---

### Post by tone77 on 2008-08-11
I figured it out.  Turns out, setting the preferred application they way I had it, was not the only way.  The fix is below:

> sudo update-alternatives --config x-www-browser
[sudo] password for anton: 

There are 4 alternatives which provide `x-www-browser'.

  Selection    Alternative
-----------------------------------------------
          1    /usr/bin/firefox-3.0
          2    /usr/bin/firefox-2
          3    /usr/bin/opera
*+        4    /usr/bin/epiphany-gecko

Press enter to keep the default[*], or type selection number: 1
Using '/usr/bin/firefox-3.0' to provide 'x-www-browser'.


It is installed now, so hopefully it will replace Evolution.

---

