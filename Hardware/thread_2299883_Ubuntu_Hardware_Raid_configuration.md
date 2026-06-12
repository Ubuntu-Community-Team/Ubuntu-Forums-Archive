---
title: "Ubuntu Hardware Raid configuration"
date: 2015-10-22
forum: Hardware
---

### Post by Antares86 on 2015-10-22
Hey

I have just recently received a new workstation. Usually I work with Macs, so I am unfortunately not very experience with dealing with hardware-related issues. I hope you can help.

Here is my setup:
MB: Supermicro with Intel C612 Express chipset
CPU: Intel Xeon E5-2650 v3 

Main drive: Intel SSD
Additional drives: 4x 4TB HDD

I simply would like to have Ubuntu run on the SSD, while having access to the hard drives as storage in a Raid 10 configuration. I have got Ubuntu 14.04 up and running on the SSD and have set up the Raid 10 with this manual:
[http://www.supermicro.com/manuals/other/Intel_PCH_RAID_Config.pdf](http://www.supermicro.com/manuals/other/Intel_PCH_RAID_Config.pdf)

The Raid setup shows up in the the configuration utility before I boot into Ubuntu. However, Ubuntu itself does not see the Raid, all I see is the 4 separate hard drives. Am I missing something here? Should I just do a software Raid with Ubuntu?

thanks for any help :)

---

