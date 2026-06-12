---
title: "Intel EtherExpress PCMCIA"
date: 2005-12-11
forum: Installation &amp; Upgrades
---

### Post by shad42 on 2005-12-11
I'm installing Ubuntu on a Sony SR7K laptop with an Intel EtherExpress pcmcia card.  I don't have a CDROM drive.  I've read reports of getting Ubuntu running on this laptop but not with this network card.

I installed Grub and the basic netboot files (linux, initrd.gz) and got the system to boot from the ramdisk.

I get the installation menus but the DHCP fails.  I have a netgear router providing DHCP.

I configured the network settings manually, but it's obviously failing to get to the network at all.  

ifconfig looks like it has the correct IP configurations.  I did notice that the Hwaddr reported by ifconfig is different than the mac address left over in the routers dhcp table when I had windows booted.

Any help would be appreciated. 

Thanks,
Shad

---

