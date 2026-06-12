---
title: "ralink, kdm and hardy"
date: 2008-11-14
forum: General Help
---

### Post by maestrobwh1 on 2008-11-14
Just a note if anyone has issues with kdm loading after compiling and installing a ralink wireless device, it seems to be that when the driver is called, it seems to be when kdm is being loaded.  Might not be an issue with gdm or xdm so I "stall" its loading by:

blacklist the device in the list in /etc/modprobe.d/blacklist

in my case it the line is 

blacklist rt2860sta

make sure it is not listed in /etc/modules

in /etc/rc.local, add a line to run a script file.  The script can be where ever you want to put it and you need to make sure it is executable.

for me it is /home/brian/bin/net

in the script you need to have something like this

#!/bin/bash
# file called "net"
sleep 3
modprobe rt2860sta 
sleep 3
ifconfig ra0 inet up
exit 0

This seems to delay it enough to avoid the lock up.

---

