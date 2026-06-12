---
title: "Problem with Hotplugging and ACPI (i guess)"
date: 2005-03-11
forum: Hardware &amp; Laptops
---

### Post by MissM@rple on 2005-03-11
I already postet this to the ubuntu users mailing list and to the german forum, but nobody had a solution yet, so I try it here and hope somebody has a clue what I can do.

I have Ubuntu on my JVC subnotebook (MP-XP731). First I installed Warty and 
everything of my hardware worked out of the box. A few days ago I updated to 
hoary (with apt-get upgrade). The new version of the hotplugging system had 
problems with finding the firmware files for my wifi card, but I googled for 
it and found a solution - i copied the files to another directory and the 
problem was gone - firmware loaded and wifi card worked again (btw. its a 
ipw2100). At this time when I fixed that problem, the notebook ran with power 
plug. Now I experienced, that when I run the notebook on batteries only, the 
problem appears again - the firmeware cannot be loaded by the hotplug system 
and thus the wifi card doesnt work. dmesg says the following:

ipw2100: Intel(R) PRO/Wireless 2100 Network Driver, 0.54
ipw2100: Copyright(c) 2003-2004 Intel Corporation
eth0: Using hotplug firmware load.
eth0: Firmware 'ipw2100-1.2.fw' not available or load failed.
eth0: ipw2100_get_firmware failed: -2
eth0: Failed to power on the adapter.
eth0: Failed to start the firmware. 

I'm pretty at a loss with this problem as I don't know where to look for what. 
Is this an ACPI-problem?

Kernel version is 2.6.8.1-3-686
Hotplug version is 0.20040329-ubuntu14
content of /proc/sys/kernel/hotplug is /sbin/udevsend

Thanks in advance
Katrin

---

### Post by alastair on 2005-03-11
I have this wireless as well. I /have/ seen this firmware failure message - but not recently and it was quite rare.

My firmware (for my kernel) :

/lib/hotplug/firmware/ipw2100-1.3-i.fw-2.6.10-4-386
/lib/hotplug/firmware/ipw2100-1.3-p.fw-2.6.10-4-386
/lib/hotplug/firmware/ipw2100-1.3.fw-2.6.10-4-386

Try removing and reinserting the driver perhaps - best to tail the systlog as you do this, to see messages as they happen i.e.

tail -f /var/log/syslog

In one shell. In another :

sudo rmmod ipw2100

sudo modprobe ipw2100

---

### Post by MissM@rple on 2005-03-13
[QUOTE=alastair]I have this wireless as well. I /have/ seen this firmware failure message - but not recently and it was quite rare.

My firmware (for my kernel) :

/lib/hotplug/firmware/ipw2100-1.3-i.fw-2.6.10-4-386
/lib/hotplug/firmware/ipw2100-1.3-p.fw-2.6.10-4-386
/lib/hotplug/firmware/ipw2100-1.3.fw-2.6.10-4-386

Try removing and reinserting the driver perhaps - best to tail the systlog as you do this, to see messages as they happen i.e.

tail -f /var/log/syslog

In one shell. In another :

sudo rmmod ipw2100

sudo modprobe ipw2100[/QUOTE]
 OK, the solution was pretty simple (thanks to Matt Zimmerman):
I used hoary packages but still the old warty kernel. Installing the linux-686 package did the trick - with the new kernel everything works well.

---

