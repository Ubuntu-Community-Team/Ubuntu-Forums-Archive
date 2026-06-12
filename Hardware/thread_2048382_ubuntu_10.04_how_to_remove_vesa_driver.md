---
title: "ubuntu 10.04 how to remove vesa driver"
date: 2012-08-26
forum: Hardware
---

### Post by linux83 on 2012-08-26
Hello All,
i have problem to run compiz and found the issue with (Vesa) driver.
the same laptop when running Ubuntu 10.04 (32-bit) it use (Intel) driver thus it work fine, however when i use ubuntu 10.04 (64bit) it use vesa dirver 
and compiz does not work.

could any one help to unload the "vesa" driver and load the right driver intel.

> *-display
             description: VGA compatible controller
             product: Intel Corporation
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 09
             width: 64 bits
             clock: 33MHz
             capabilities: bus_master cap_list rom
             configuration: driver=i915 latency=0
             resources: irq:18 memory:f0000000-f03fffff memory:e0000000-efffffff ioport:5000(size=64) 			 		

>  			 				00:02.0 VGA compatible controller [0300]: Intel Corporation Device [8086:0116] (rev 09) 			 		

working system:

> Gathering information about your system...
 Distribution:          Ubuntu 10.04
 Desktop environment:   GNOME
 Graphics chip:         Intel Corporation Device 0116 (rev 09)
 Driver in use:           intel
 Rendering method:  AIGLX


Non-working system:

> Gathering information about your system...
 Distribution:          Ubuntu 10.04
 Desktop environment:   GNOME
 Graphics chip:         Intel Corporation Device 0116 (rev 09)
 Driver in use:           vesa
 Rendering method:  AIGLX


thanks alot for any help.

linux83

---

### Post by linux83 on 2012-08-27
Hello, 
this to update my case and might help some one else:

you will be unable to remove or unload the vesa driver even if you block it from module black list or remove the xserver from sypantic manager if your driver is (intel), what i did is just install the latest intel driver:

> sudo add-apt-repository ppa:glasen/intel-driver
 sudo apt-get update
 sudo apt-get upgrade

reference:
[http://askubuntu.com/questions/4658/how-to-install-intel-82852-855gm-driver](http://askubuntu.com/questions/4658/how-to-install-intel-82852-855gm-driver)

it save my day.


linux83

---

