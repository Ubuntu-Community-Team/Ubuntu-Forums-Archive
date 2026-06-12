---
title: "Problem with Changing IP address"
date: 2008-08-08
forum: General Help
---

### Post by rolandsym on 2008-08-08
Hello,
   I hope this is the area for this question type.

   I have Ubuntu 8.04 Desktop installed.  I am having a problem changing the IP address, adding users, etc... basicly changing any setting in the GUI that requires authentication.  When I put in the proper information the GUI locks up.  If I screw up my password then it just fails.  I know I can use the command line to do this and previously this was all working until today.  I'm new to the Ubuntu Desktop scene but I have some general Linux experience.  Any help in this would be appreciated.

Rolandsym

---

### Post by pytheas22 on 2008-08-08
You can set your IP from the command-line using ipconfig, e.g.:
```

sudo ifconfig eth0 192.168.1.2
```

(change 'eth0' to the name of the relevant interface--eth0 is usually ethernet; wireless would probably be 'eth1' or 'wlan0,' or possibly other things, depending on your particular wireless card).  The new IP will only last till the next reboot; if you need to change the IP permanently, you have to edit /etc/network/interfaces.

I suspect that your issue with the GUI locking up might have to do with a bug in the GUI more than the underlying applications that are being called by the GUI.  Does it only lockup when you're trying to do networking stuff through the GUI, or other times as well?  For instance, can you open Synaptic or the Users and Groups GUI (both under System>Administration) without issues?

---

