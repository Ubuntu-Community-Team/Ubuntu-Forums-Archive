---
title: "Wired Network Device Not Managed"
date: 2009-09-15
forum: Installation &amp; Upgrades
---

### Post by f00b on 2009-09-15
I installed Ubuntu 9 on a dell inspiron 531S a while back, and I'm just getting around to working with it the way i originally wanted to.

I booted it up today and I am having trouble reaching the internet.  I have it connected via ethernet cable, and the light is blinking on the back of the computer notating that the internet connection is live.  I also plugged in a laptop i have to check to make sure the wired network is working and it is in fact working fine. I was able to access the internet on with this connection.

However, in ubuntu i cannot access the internet.  When i click the network button at the top right of the menu bar it says

"Wired Network
Device Not Managed"

any ideas how i can get to the bottom of this one?

---

### Post by abouzar on 2009-09-15
Try restarting the network manager by:

```
sudo /etc/init.d/networking restart
```

If the problem persists go to:
System--> Administration--> Networking Tools

to see if your Ethernet card is working properly.

---

### Post by f00b on 2009-09-16
I did what you suggested and this is what came up

----------------------------------------------------------------
* Reconfiguring network interfaces...                                          RTNETLINK answers: No such process
postconf: fatal: open /etc/postfix/main.cf: No such file or directory
There is already a pid file /var/run/dhclient.eth0.pid with pid 2961
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.1.1
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth0/00:21:70:6d:a6:b4
Sending on   LPF/eth0/00:21:70:6d:a6:b4
Sending on   Socket/fallback
DHCPRELEASE on eth0 to 192.168.1.1 port 67
send_packet: Network is unreachable
send_packet: please consult README file regarding broadcast address.
Internet Systems Consortium DHCP Client V3.1.1
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth0/00:21:70:6d:a6:b4
Sending on   LPF/eth0/00:21:70:6d:a6:b4
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
DHCPOFFER of 192.168.1.48 from 192.168.1.1
DHCPREQUEST of 192.168.1.48 on eth0 to 255.255.255.255 port 67
DHCPACK of 192.168.1.48 from 192.168.1.1
bound to 192.168.1.48 -- renewal in 38522 seconds.
postconf: fatal: open /etc/postfix/main.cf: No such file or directory
                                                                         [ OK ]

---------------------------------------------------------------

and then network still doesn't work.

---

### Post by antony_css on 2009-10-12
/etc/NetworkManager/nm-system-settings.conf should look like:
```

[main]
plugins=ifupdown,keyfile

[ifupdown]
managed=false

```

Change the value of **managed** from false to true, using any text editor you like ( I prefer vim). Now restart your computer and the problem should settle.

I found that solution from a closed thread: 
[http://ubuntuforums.org/showthread.php?t=1109585&highlight=device+not+managed+network+manager+wired]("http://ubuntuforums.org/showthread.php?t=1109585&highlight=device+not+managed+network+manager+wired")

---

### Post by shredder12 on 2009-10-12
I am not sure about your problem..
but i faced a similar problem when i configure the /etc/network/interface file manually (i actually configured pppoe modem)..
Plz.. remember if you have configured the file manually the last time you used it...
This article says a similar thing.. <snip>

---

### Post by f00b on 2009-10-15
I tried changing the /etc/NetworkManager/nm-system-settings.conf file from

[ifupdown]
managed=false

To

[ifupdown]
managed=true

I restarted and now there are three devices in the "Wired Networks" button in the taskbar.  They are listed as

Wired Connection 1
Wired Connection 2
Ifupdown (eth0)

Where the Ifupdown (eth0) is the one selected.  I still do not have internet on this computer... 

I tried also doing a 
%sudo lshw -C network
Result:
*-network DISABLED
description: Ethernet interface
physical id: 1
logical name: pan0
serial: 06:20:62:...
capabilities: ethernet physical
configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes mulicast=yes

Not sure what this means, anyone got any ideas?

---

### Post by Iowan on 2009-10-15
pan0 is Personal Area Network (bluetooth).
What is in */etc/network/interfaces*?

---

### Post by gm.matias on 2009-12-25
I had the same problem and this worked for me: [http://www.gmmatias.com/device-not-managed-status-in-wired-networks-2009-12-07](http://www.gmmatias.com/device-not-managed-status-in-wired-networks-2009-12-07)

---

