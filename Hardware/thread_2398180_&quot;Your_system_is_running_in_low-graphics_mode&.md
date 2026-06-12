---
title: "&quot;Your system is running in low-graphics mode&quot; after every reboot"
date: 2018-08-08
forum: Hardware
---

### Post by jolindbe on 2018-08-08
Hi,

I've had this problem for quite a while now - actually since a software update back in April. Since it is only occurs at reboot and can easily be bypassed I haven't got around to trying to solve it until now...

At every reboot I would get a "Your system is running in low-graphics mode" message, and after selecting "Try running with default graphics mode" the bootup completes normally, and I don't see this until the next reboot. 

I have a Lenovo Thinkpad T430s running Ubuntu 16.04 LTS.

Some info from lshw about the graphics card:

> 
  *-display               
       description: VGA compatible controller
       product: 3rd Gen Core processor Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 09
       width: 64 bits
       clock: 33MHz
       capabilities: msi pm vga_controller bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: irq:27 memory:f0000000-f03fffff memory:e0000000-efffffff ioport:5000(size=64)


Coincidentally, at the same time this bug started, another bug also started. [I have posted about that one in a more relevant sub-forum]("https://ubuntuforums.org/showthread.php?t=2398178&p=13790416#post13790416"), but in case it would be related (which sounds unlikely): Every time I boot my laptop it refuses to see any wireless networks. Ethernet is fine. "Enable Wi-Fi" is selected in the menu bar, but it doesn't find any networks at all. Rebooting does not help. Running "sudo service network-manager restart" solves the problem until the next reboot.

Please let me know if you need more info, outputs, etc. Many thanks!!

---

### Post by Autodave on 2018-08-08
I doubt this will help, but it is worth a shot.  And it is the very first thing that I do when I get a laptop that something has quit working properly....especially when that something used to work just fine.

Power down and remove EVERY cord. Remove battery. Wait 10 minutes and put the battery back in and connect the power cord only.  Power up and see if that does any good. Then, you can reconnect any other cords you disconnected.

---

### Post by jolindbe on 2018-08-09
Nope, that did not help (both problems remain). Thanks for the suggestion, though.

---

### Post by jolindbe on 2018-08-17
Upgrading to 18.04 seems to have fixed both issues.

---

