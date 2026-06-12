---
title: "FayTun USB WiFi adapter not working"
date: 2018-10-04
forum: Hardware
---

### Post by moetele on 2018-10-04
Hi guys and gals:

new to Ubuntu.. 

reading previous posts, you need to know a little bit about the adapter:
I need help with usb FayTun WIFI adapter
command "lshw -C network" does not display any info for it.


Output from "lshw" shows that the device is UNCLAIMED
           *-usb:1 UNCLAIMED
                description: Generic USB device
                product: 802.11ac NIC
                vendor: Realtek
                physical id: 5
                bus info: usb@1:5
                version: 2.10
                serial: 123456
                capabilities: usb-2.10
                configuration: maxpower=500mA speed=480Mbit/s

Info for the system:

lsb_release:
No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 16.04.5 LTS
Release:        16.04
Codename:       xenial

uname -r:
greg@tartan:/tmp$ uname -r
4.4.0-137-generic

apt list --installed | grep linux-firmware*


WARNING: apt does not have a stable CLI interface. Use with caution in scripts.


linux-firmware/xenial-updates,xenial-updates,now 1.157.20 all [installed,automatic]

I'm not really sure where to go from here.....
Can someone please help?

Thanks,
-Greg

---

### Post by moetele on 2018-10-04
Does the fact that is shows up as Realtek mean that I can use a Realtek driver with it?  Is there a generic Realtek driver?

---

### Post by moetele on 2018-10-05
I finally found the original packaging for it..  it says it's a FayTun 1200Mbps Wireless USB adapter.
The small CD that came with is has some LINUX drivers on it.  They say RTL88x2BU_WiFi_linux_v5.2.4.1_22719_COEX20170518-4444
When I run the install.sh script that is there, it goes through and tries to compile and says:
Makefile:320: recipe for target 'build_tools' failed

What am I doing wrong?

---

### Post by moetele on 2018-10-05
I found it!!!  Earlier up in the list it kept complaining about bc not being found.  I did sudo apt-get install bc
Reran the install.sh script and rebooted.  Now I have a wireless adapter installed.

Just need to configure it to start up and obtain an IP address.

---

