---
title: "Installation Issue on Dell Optiplex 740"
date: 2007-04-10
forum: Hardware &amp; Laptops
---

### Post by jchadwick on 2007-04-10
Hello,
I am trying to install Ubuntu Dapper (6.06) AMD64 on a brand new Dell Optiplex 740 workstation (AMD64 Athlon X2).  During the installation process, there is a problem detecting the network card.  The message that I receive is:

"Detect Network Hardware
No ethernet card was detectedm but a FireWire interface is present.  It's possible though unlikely, that with the right FireWire hardware connected to it, this could be your primary ethernet interface.  Do you intend to use FireWire Ethernet?  <YES> / <NO>"

If I hit No, I get a bright red screen that says "No network interfaces detected".

Has anyone had a similar issue, and is there a fix available?

Thanks for the assistance.

Jordan

---

### Post by caffienefree on 2007-04-10
Did you continue the installation past this point?

---

### Post by jchadwick on 2007-04-11
Hello,
Yes, I did initially.  When the system booted up for the first time, there were no interfaces listed when I did an ifconfig besides the loopback interface.  Is it possible the interface is listed in /dev and just not enabled?

BTW, I am using the server installation, so I can only use terminal commands to try to troubleshoot this issue.

Thanks for the assistance.

Jordan

---

### Post by caffienefree on 2007-04-11
Could you please post the output of:

sudo lshw -C network

---

### Post by jchadwick on 2007-04-12
Hello,
Here is the output of the command:

[366.595669] Buffer I/O error on device sr0, logical block 0
[366.602443] Buffer I/O error on device sr0, logical block 1
[366.609113] Buffer I/O error on device sr0, logical block 2
[366.615766] Buffer I/O error on device sr0, logical block 3
[366.622064] Buffer I/O error on device sr0, logical block 4
[366.628044] Buffer I/O error on device sr0, logical block 5
[366.628047] Buffer I/O error on device sr0, logical block 6
[366.628049] Buffer I/O error on device sr0, logical block 7
[366.628051] Buffer I/O error on device sr0, logical block 8
[366.628053] Buffer I/O error on device sr0, logical block 9
*-network UNCLAIMED
	description: Ethernet controller
	product: Broadcom Corporation
	vendor: Broadcom Corporation
	physical id: 0
	bus info: pci@02:00.0
	version: 02
	width: 64 bits
	clock: 33 MHz
	capabilities: bus_master cap_list
	resources: iomemory:fdef0000-fdefffff irq:14


Thanks,
Jordan

---

### Post by caffienefree on 2007-04-12
Please give this guide a try.

[http://ubuntuforums.org/showthread.php?t=201902](http://ubuntuforums.org/showthread.php?t=201902)

You're going to need to get your driver from the dell manufacturers site though (It should be two files, something.inf and something.sys).

---

### Post by water8 on 2007-10-19
I have same problem using 6.06 server on Asus M2A-VM. The error message is "No ethernet card was detected, but a FireWire Interface is present."  

My quick fix is to use 7.10. And it works!

---

