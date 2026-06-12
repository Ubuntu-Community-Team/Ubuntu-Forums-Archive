---
title: "How To Enable AMD Radeon Dynamic Power Management (DPM) In Ubuntu 13.10"
date: 2014-01-25
forum: Hardware
---

### Post by SurfaceUnits on 2014-01-25
**The open source AMD Radeon driver  got dynamic power management support with Linux Kernel 3.11. With this,  the GPU and memory clocks adjust dynamically based on load, useful for  saving power.**

[B]This feature is not enabled by  default, at least in Ubuntu 13.10 (it will probably be enabled by  default in Ubuntu 14.04) so here's how to enable it.

[http://www.webupd8.org/2014/01/how-to-enable-amd-radeon-dynamic-power.html](http://www.webupd8.org/2014/01/how-to-enable-amd-radeon-dynamic-power.html)
[/B]

---

### Post by Yellow Pasque on 2014-01-26
These instructions have existed for a while: [https://help.ubuntu.com/community/RadeonDriver#Kernel_3.11.x_.28Ubuntu_13.10.2BAC8-Saucy.29_and_Later](https://help.ubuntu.com/community/RadeonDriver#Kernel_3.11.x_.28Ubuntu_13.10.2BAC8-Saucy.29_and_Later)
Unfortunately, most people don't know the term "DPM" and won;t find the instructions even if it solves their overheating issues

Hopefully, Ubuntu 14.04 will get its stuff together and enable DPM (even if some cards have issues with it), vdpau in mesa, etc. so people don't need hacks like that.
oibaf's PPA is also worth a mention for radeon users: [https://launchpad.net/~oibaf/+archive/graphics-drivers](https://launchpad.net/~oibaf/+archive/graphics-drivers)

---

### Post by pme 72 on 2014-02-02
Enabling dpm on 13.10 worked with an ATI HD 4550 in my desktop but I noticed:

1. Resume from Suspend left the graphics in a workable but less than optimal state though rebooting restored full functionality.
2. The cooling fins on the integrated ATI HD 3000 RS780 seemed to be hot all the time (whether or not dpm was enabled).
3. When I pulled out the 4550 it occurred to me that the physical presence of the card could be interfering with natural case air flow cooling to the integrated HD 3000.
4. dpm seems to work flawlessly with just the HD 3000 and the cooling fins are now barely warm with regular usage. 
5. After playing a few rounds of SuperTuxKart or Cannon Smash the HD 3000 shifts to an appropriate lower performance state quickly as did the HD 4550.
6. There was an unexpected performance improvement with the HD 3000 compared to its performance before enabling dpm.

---

