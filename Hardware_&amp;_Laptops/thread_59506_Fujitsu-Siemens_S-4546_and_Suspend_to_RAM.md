---
title: "Fujitsu-Siemens S-4546 and Suspend to RAM"
date: 2005-08-24
forum: Hardware &amp; Laptops
---

### Post by laserline on 2005-08-24
Hello all,

I have a problem with suspend to ram...
The laptop shutsdown and all ok, but when i wake it up network breaks.
Suspend to disk (Hibernate) works ok after adding the #kopt line "resume=/dev/hda5"

When i run the sudo /etc/acpi/sleep.sh I get the following: (this is the full output, after the computer is back from suspension)
------------------------------------------------------------------------------------------------
~$ sudo /etc/acpi/sleep.sh
Internet Systems Consortium DHCP Client V3.0.1
Copyright 2004 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

sit0: unknown hardware address type 776
sit0: unknown hardware address type 776
Listening on LPF/eth0/00:00:0e:21:22:c4
Sending on   LPF/eth0/00:00:0e:21:22:c4
Sending on   Socket/fallback
DHCPRELEASE on eth0 to 213.57.35.2 port 67
Unknown id: laserlin
Xlib: connection to ":0.0" refused by server
Xlib: No protocol specified

xset:  unable to open display ":0"
Warning: Interface name is `eth0' at line 2, can't be mapped reliably.
Internet Systems Consortium DHCP Client V3.0.1
Copyright 2004 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

sit0: unknown hardware address type 776
SIOCSIFADDR: No such device
eth1: ERROR while getting interface flags: No such device
Unknown id: laserlin
eth1: ERROR while getting interface flags: No such device
laserline@ubuntu-laptop:~$ sit0: unknown hardware address type 776
Bind socket to interface: No such device
Failed to bring up eth1.
Internet Systems Consortium DHCP Client V3.0.1
Copyright 2004 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

sit0: unknown hardware address type 776
SIOCSIFADDR: No such device
eth0: ERROR while getting interface flags: No such device
eth0: ERROR while getting interface flags: No such device
sit0: unknown hardware address type 776
Bind socket to interface: No such device
Failed to bring up eth0.
----------------------------------------------------------------------------------------------
The problem is that even "sudo /etc/init.d/network restart" or force-restart and "sudo /etc/init.d/ifupdown restart" or force-restart doesn't help, and only rebooting the computer makes my network interface back up. 

I noticed that after suspending to ram, trying to restart the system from gnome, it hangs after terminating all processes (mentioning the eth0 cannot be found) on the line "restarting system" and I have to turn it off manually from the power button...

Help would be appriciated.

Idan. ](*,)

---

