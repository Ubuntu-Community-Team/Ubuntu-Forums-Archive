---
title: "USB wlan device not recognized"
date: 2010-06-18
forum: Hardware
---

### Post by tpeelen on 2010-06-18
I can not get my Sweex Wireless 300N Adapter USB working. Tried several things:
[LIST]
[*]out of the box it worked fine for 802.11g networks but I missed my 802.11n network
[*]found how to install the Sweex Windows-driver using the ndis-wrapper NDISGTK
[*]using its 64bit lw3x3_xpx64 driver seemed to work fine (could connect to my router) but after rebooting it seemed to keep on connecting forever. Gnome itself responded very slow.
[*]After uninstalling NDISGTK (and tools and common scripts) I could not get back to my starting situation: WLAN did not work for any 802.11x network
[*]Installed wireless-tools like explained at [https://help.ubuntu.com/community/WifiDocs/WiFiHowTo](https://help.ubuntu.com/community/WifiDocs/WiFiHowTo) but did not find a network card ofcourse
[*]In the end figured out I should be using lsusb instead of lspci but found no information on the device except it's ID (see below)
[*]Also tried reinstalling NDISGTK but still the same effect: the device is not working
[/LIST]

My current situation is as follows:
[LIST]
[*]using Ubuntu 10.4 (latest updates installed)
[*]lsusb displays the ID being ID 177f:0313
```
tpeelen@CC-desktop:/dev/usb$ lsusb 
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 002: ID 046d:c517 Logitech, Inc. LX710 Cordless Desktop Laser
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 004: ID 177f:0313  
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
tpeelen@CC-desktop:/dev/usb$
```

[*]

My device drivers seem to function
[IMG]http://www.open-consult.nl/download/ndisgtk.png[/IMG]

[*]

WLAN can not be enabled
[IMG]http://www.open-consult.nl/download/notenabled.png[/IMG]

[*]

WLAN can not be discovered
[IMG]http://www.open-consult.nl/download/nodiscovery.png[/IMG]
[/LIST]

Obviously I'm doing something wrong. However I cannot discover what. 

I appreciate your help.

Tom.

---

### Post by tpeelen on 2010-06-19
I found one mistake I made: Only one of the drivers is tried. My boot.log clearly showed it could not load a ndiswrapper driver. Removing them one at a time I discovered the one driver that would load. 

However this brought me at the next problem. It blocks the network deamon resulting in a stack trace after two minutes. Because the different nature of this problem I close this posting.

---

### Post by tpeelen on 2010-06-19
If you're interested in my new post please visit 
[INDENT][_ndisgtk blocks network manager for 120 seconds and causes stack trace_]("http://ubuntuforums.org/showthread.php?p=9483114#post9483114")[/INDENT]

---

