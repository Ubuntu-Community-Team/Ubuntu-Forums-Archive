---
title: "Tp-fancontrol On Thinkpad T61"
date: 2008-07-05
forum: Hardware
---

### Post by woodeast on 2008-07-05
Hey, I'm a converted Gentoo user who's really lovin' how Ubuntu "just works". 

Here goes nothing, my first post:

I'm having a hard time getting the tp-fancontrol script working under my T61 laptop. 

**System info:**

> Ubuntu 8.04, Hardy Heron
Kernel Linux 2.6.24-16 generic 

**What I've Done**

- Gotten the latest tp-fancontrol script from ThinkWiki
- chmod +x to made the script executable
- modprobe ibm_acpi experimental=1
- modprobe thinkpad_acpi experimental=1 fan_control=1

**Result**

> 
root@ubuntu:/home/ubuntu/Desktop# ./tp-fancontrol 
16055: old priority 0, new priority -10
> Starting dynamic fan control
./tp-fancontrol: line 242: /proc/acpi/ibm/ecdump: No such file or directory
> Shutting down, switching to automatic fan control
./tp-fancontrol: line 257: /proc/acpi/ibm/ecdump: No such file or directory


Help! I've struggled a long time for this. Thanks in advance.

---

### Post by woodeast on 2008-07-05
Problem solved.
[B]
Solution:[/B]

Edit (or create new) /etc/modprobe.conf file:

> sudo nano /etc/modprobe.conf
options thinkpad_acpi experimental=1 fan_control=1

Then reboot and config as needed (see ThinkWiki)

---

