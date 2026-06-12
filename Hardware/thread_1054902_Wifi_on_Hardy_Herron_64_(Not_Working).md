---
title: "Wifi on Hardy Herron 64 (Not Working)"
date: 2009-01-30
forum: Hardware
---

### Post by Robster2 on 2009-01-30
I have a Toshiba with AMD 64 Turion x2 processor. L300 Laptop

I know this question has been posted several times,  however, I find that in each method posted something about it is out of date.   


DOES ANYBODY HAVE A METHOD THAT WORKS - NOW???



Back ground stuff:

I have tried about five different methods laid out in step by step format.

All of them have some fatal error.   Madwifi keeps changing the locations of their files.

 svn co [http://snapshots.madwifi-project.org/madwifi-hal-0.10.5.6](http://snapshots.madwifi-project.org/madwifi-hal-0.10.5.6)
svn: PROPFIND request failed on '/madwifi-hal-0.10.5.6'
svn: PROPFIND of '/madwifi-hal-0.10.5.6': 301 Moved Permanently ([http://snapshots.madwifi-project.org](http://snapshots.madwifi-project.org))


rob@rob-laptop:~$ sudo lshw -C network 
[sudo] password for rob:

   *-network UNCLAIMED
       description: Ethernet controller
       product: AR242x 802.11abg Wireless PCI Express Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:05:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix cap_list
       configuration: latency=0

---

