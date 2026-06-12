---
title: "Setting up a 3 internal fax server on 10.04 LTS"
date: 2011-06-22
forum: Hardware
---

### Post by riig007 on 2011-06-22
I hope someone can guide me as to what else to try.
I have setup a box with 3 internal winmodems on a ubuntu 10.04 LTS.

I ran scanmodem and it identified the modems as follows:

[I]Candidate PCI devices with modem chips are:
01:04.0 Communication controller: Agere Systems LT WinModem
01:05.0 Communication controller: Agere Systems LT WinModem
01:06.0 Communication controller: Agere Systems 56k WinModem (rev 01)
High Definition Audio cards can host modem chips.[/I]

I have intsalled the martian-modem and martian-modem-source packages straight from 
ubuntu packages, but it does not help detecting the modems.  I believe there is something I have to do.

I am using the webmin GUI and installed the Hylafax package, but Hylafax will not recognize the modems.  I installed the latest headers packages associated with the kernel (ie. 2.6.32-32-generic-pae).  I also installed the build-essential package since I tried to compile the martian package from scratch as well.

At this point, I am not sure what else to do, but I know, from what I have read, that people have been able to get these winmodems to work on 10.04 LTS.

Any ideas about what else I should try? Any help is greatly appreciated.

UPDATE:

I have tried a couple more things and I am close to getting this 
faxserver up and running.

I had to install the "quilt" package and the "debhelper" package in 
order to build martian.

Then I followed the instructions on the README/DEBIAN file of martian that say:
[B]
> dmesg | grep martian[/B] 

[    8.554117] martian loaded - 20080620 
[    8.554213] martian 0000:01:04.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16 
[    8.554249] martian: added device 11c1:44e BaseAddress = 0xdc00, 
CommAddres = 0xdbe8, irq = 16 
[    8.554267] martian 0000:01:05.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17 
[    8.554299] martian: added device 11c1:44e BaseAddress = 0xdd00, 
CommAddres = 0xdbf0, irq = 17 
[    8.554315] martian 0000:01:06.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18 
[    8.554335] martian: added device 11c1:442 BaseAddress = 0xde00, 
CommAddres = 0xdbf8, irq = 18 
[    9.698609] martian_modem is attached. 
[62452.261226] martian_modem is detached 
[62457.721736] martian_modem is attached. 
[63071.533033] martian_modem is detached 
[63736.509611] martian_modem is attached. 

I am kind of stuck at this point.  I will keep researching and will post later.

---

