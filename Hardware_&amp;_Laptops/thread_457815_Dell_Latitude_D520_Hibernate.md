---
title: "Dell Latitude D520 Hibernate?"
date: 2007-05-29
forum: Hardware &amp; Laptops
---

### Post by matthinckley on 2007-05-29
Hi all,

I have a Dell Latitude D520 with Feisty installed.. Suspend works without a hitch but I can't get the computer to hibernate.  pops back to gnome and gives me error about HAL and to check the Help FAQ.. 

here is the output when I run /etc/acpi/hibernate.sh:

```
matt@sutherland:~$ sudo /etc/acpi/hibernate.sh 
Password:
RTNETLINK answers: No such process
There is already a pid file /var/run/dhclient.eth0.pid with pid 9241
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/eth0/00:19:b9:5d:6a:b5
Sending on   LPF/eth0/00:19:b9:5d:6a:b5
Sending on   Socket/fallback
ifdown: interface eth1 not configured
ifdown: interface eth0:avah not configured
SIOCSIFFLAGS: Cannot assign requested address
Allocated buffer at 0x2010 (base is 0x0)
ES: 0x0201 EBX: 0x0000
 * Shutting down ALSA...                                                 [ OK ] 
/etc/acpi/hibernate.sh: line 39: echo: write error: No such device
Laptop mode disabled, not active.
Function not supported
ifup: interface eth0 already configured
Ignoring unknown interface eth1=eth1.
Ignoring unknown interface eth0:avah=eth0:avah.
 * Setting up ALSA...                                                    [ OK ] 
grep: /proc/acpi/fan/*/state: No such file or directory
FATAL: Module acpi_sbs not found.
FATAL: Module acpi_sbs not found.
matt@sutherland:~$ 

```

Any ideas?

Thanks.

Matt

---

### Post by scotthanson on 2007-06-01
I don't have the answer, but I'm having the same problem. Here's the relevant output after running /etc/acpi/hibernate.sh:

```

<snip>
Shutting down ALSA...done.
Usage: suspend [-f config][resume_device]
Laptop mode disabled, not active.
/etc/acpi/resume.d/17-video-restore.sh: line 5: /var/lib/acpi-support/vbestate: No such file or directory
Function not supported
ifup: interface eth0 already configured
Ignoring unknown interface eth1=eth1.
Setting up ALSA...done.
grep: /proc/acpi/fan/*/state: No such file or directory
FATAL: Module acpi_sbs not found.
FATAL: Module acpi_sbs not found.
```

I also get the "HAL failed to hibernate" message from the Gnome power manager.

I'm running Feisty on an ASUS M6Ne laptop, latest BIOS version. It has a 1.8 GHz Centrino with 1024 MB RAM and an ATI Mobility Radeon 9700. I am using fglrx, and have all the latest Ubuntu updates installed.

---

### Post by scotthanson on 2007-06-01
One idea is to try uswsusp instead of the standard hibernate script. It works much better for me, though still not 100% reliable.

See [http://blog.paulbetts.org/index.php/2007/02/11/fixing-software-suspend-hibernate-with-uswsusp-in-ubuntu-feisty-and-edgy/]("http://blog.paulbetts.org/index.php/2007/02/11/fixing-software-suspend-hibernate-with-uswsusp-in-ubuntu-feisty-and-edgy/") for instructions.

---

### Post by matthinckley on 2007-06-01
> **scotthanson said:**
> One idea is to try uswsusp instead of the standard hibernate script. It works much better for me, though still not 100% reliable.

See [http://blog.paulbetts.org/index.php/2007/02/11/fixing-software-suspend-hibernate-with-uswsusp-in-ubuntu-feisty-and-edgy/]("http://blog.paulbetts.org/index.php/2007/02/11/fixing-software-suspend-hibernate-with-uswsusp-in-ubuntu-feisty-and-edgy/") for instructions.

Thanks! works great for me!

---

