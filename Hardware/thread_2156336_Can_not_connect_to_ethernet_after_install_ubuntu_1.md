---
title: "Can not connect to ethernet after install ubuntu 10.04"
date: 2013-06-21
forum: Hardware
---

### Post by kimalighten on 2013-06-21
Hi all, 

I have got a trouble here. After reinstall ubuntu10.04, it just cannot connect to internet(with wire). ifconfig gives: lo ....which is very wired. The nci is enabled in bois. Any suggestions? I'm using Dell optiplex 7010.

---

### Post by TheFu on 2013-06-21
Can you run off the LiveCD - not the installed Ubuntu? Does networking work properly?

The lo device is a loopback - not using any NIC.  Usually the NIC device is "eth0."
What do the log files show about your networking?
What does the boot log show about your networking?
Are any network devices seen by the OS? Run **sudo lshw -C network** to see. Please post that output.
What does the full **ifconfig** output show?

---

### Post by kimalighten on 2013-06-21
ifconfig&#65306;
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:12 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:720 (720.0 B)  TX bytes:720 (720.0 B)

[B]sudo lshw -C network
[/B] *-network UNCLAIMED     
       description: Ethernet controller
       product: Intel Corporation
       vendor: Intel Corporation
       physical id: 19
       bus info: pci@0000:00:19.0
       version: 04
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi bus_master cap_list
       configuration: latency=0
       resources: memory:f7f00000-f7f1ffff memory:f7f39000-f7f39fff ioport:f040(size=32)



boot.log


fsck from util-linux-ng 2.17.2
/dev/sda1: clean, 136126/59555840 files, 4304764/238222336 blocks
 * Starting AppArmor profiles       [80G Skipping profile in /etc/apparmor.d/disable: usr.bin.firefox


[74G[ OK ]
 * Setting sensors limits       [80G 
[74G[ OK ]
 [33m*[39;49m Speech-dispatcher configured for user sessions
 * Starting Common Unix Printing System: cupsd       [80G 
[74G[ OK ]
 [33m*[39;49m PulseAudio configured for per-user sessions
 * Enabling additional executable binary formats binfmt-support       [80G

---

### Post by kimalighten on 2013-06-21
I solved this by install e1000e driver on the platform.

---

### Post by TheFu on 2013-06-21
Ok, so it appears that your ethernet controller isn't recognized. No driver is loaded for it.  Unfortunately, the **lshw** command would be the way that I would ask to determine which chip the NIC used. It isn't saying anything, so you need to figure that out manually some other way - perhaps getting a parts list from Dell?

Then you need to manually load the kernel driver.  That usually means adding the driver to the  /etc/modprobe.d/ or /etc/modules files.

Until the correct NIC driver is loaded into the kernel, you are stuck.

---

### Post by mörgæs on 2013-06-22
Are you aware that 10.04 is out of support?

---

### Post by TheFu on 2013-06-22
> **mörgæs said:**
> Are you aware that 10.04 is out of support?

Isn't only 10.04 Desktop out of support?  Pretty much anyone running 10.04 desktop should migrate to 12.04 LTS desktop - which gets 5 yrs of support (2017).

10.04 Server has 2 more years of support - heck, I'm running more than a few 10.04 servers now, so I hope it is still getting patched until 2015-ish.

---

### Post by mörgæs on 2013-06-22
Correct, but as Firefox was mentioned above this must be a desktop installation.

---

