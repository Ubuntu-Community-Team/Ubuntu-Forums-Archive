---
title: "Sleep button in T42 not working"
date: 2007-02-25
forum: Hardware &amp; Laptops
---

### Post by MasterOfMuppets on 2007-02-25
Hi all!
Running KDE edgy on a T42 thinkpad here, and the sleep FN+F4 doesn't work.
But, as shown below, I can run the sleep script and I get this:

```
moshewe@moshewe-laptop:/$ sudo /etc/acpi/sleep.sh
 * Stopping powernowd:                                                   [ ok ]
postconf: fatal: open /etc/postfix/main.cf: No such file or directory
There is already a pid file /var/run/dhclient.eth0.pid with pid 5646
removed stale PID file
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/eth0/00:01:6c:e9:cf:e9
Sending on   LPF/eth0/00:01:6c:e9:cf:e9
Sending on   Socket/fallback
DHCPRELEASE on eth0 to 192.168.1.1 port 67
postconf: fatal: open /etc/postfix/main.cf: No such file or directory
There is already a pid file /var/run/dhclient.eth1.pid with pid 5627
removed stale PID file
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/eth1/00:15:00:3c:f6:96
Sending on   LPF/eth1/00:15:00:3c:f6:96
Sending on   Socket/fallback
DHCPRELEASE on eth1 to 192.168.1.1 port 67
postconf: fatal: open /etc/postfix/main.cf: No such file or directory
 * Shutting down ALSA...                                                 [ ok ]
Calling INT 0x15 (F000:66DE)
 EAX is 0x5F08
Calling INT 0x15 (F000:66DE)
 EAX is 0x5F08
Calling INT 0x15 (F000:66DE)
 EAX is 0x5F08
Calling INT 0x15 (F000:66DE)
 EAX is 0x5F08
Calling INT 0x15 (F000:66DE)
 EAX is 0x5F08
Calling INT 0x15 (F000:66DE)
 EAX is 0x5F08
Calling INT 0x15 (F000:66DE)
 EAX is 0x5F08
Calling INT 0x15 (F000:66DE)
 EAX is 0x5F08
Calling INT 0x15 (F000:66DE)
 EAX is 0x5F08
Calling INT 0x15 (F000:66DE)
 EAX is 0x5F08
Calling INT 0x15 (F000:66DE)
 EAX is 0x5F08
Calling INT 0x15 (F000:66DE)
 EAX is 0x5F08
Function not supported
Calling INT 0x15 (F000:66DE)
 EAX is 0x5F08
Function not supported
Calling INT 0x15 (F000:66DE)
 EAX is 0x5F08
ifup: interface eth0 already configured
ifup: interface eth1 already configured
 * Setting up ALSA...                                                    [ ok ]
grep: /proc/acpi/fan/*/state: No such file or directory
FATAL: Module acpi_sbs not found.
FATAL: Module acpi_sbs not found.
 * Starting powernowd...                                                 [ ok ]
moshewe@moshewe-laptop:/$             
```

Any idea what's going on?
Do I have to bind the keys to the script manually?

---

### Post by jazzgossen on 2007-03-14
I have the same problem on a new Feisty installation. Hibernation worked under Edgy, though. I have a Dell Latitude D800. Whether I click the gnome hibernate button or run "sudo /etc/acpi/hibernate.sh", I get a black screen briefly and then get thrown back to my X session.

Terminal output posted below.

```
~> sudo /etc/acpi/hibernate.sh
Password:
There is already a pid file /var/run/dhclient.eth1.pid with pid 5297
removed stale PID file
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/eth1/00:0c:f1:14:93:37
Sending on   LPF/eth1/00:0c:f1:14:93:37
Sending on   Socket/fallback
 * Shutting down ALSA...                                                 [ OK ] 
Usage: suspend [-f config][resume_device]
Laptop mode disabled, not active.
Function not supported
Function not supported
ifup: interface eth0 already configured
ifup: interface eth1 already configured
 * Setting up ALSA...                                                    [ OK ] 
grep: /proc/acpi/fan/*/state: Filen eller katalogen finns inte
FATAL: Module acpi_sbs not found.
FATAL: Module acpi_sbs not found.

~> 

```

---

