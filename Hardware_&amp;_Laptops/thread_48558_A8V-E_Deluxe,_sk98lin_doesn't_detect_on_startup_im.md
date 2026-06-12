---
title: "A8V-E Deluxe, sk98lin doesn't detect on startup immediately"
date: 2005-07-13
forum: Hardware &amp; Laptops
---

### Post by ravuya on 2005-07-13
Hi,

I built the sk98lin driver from source (latest version) to manage the Marvell gigabit ethernet controller on my new Asus A8V-E Deluxe logic board. If I put it in /etc/modules, it doesn't detect the hardware on startup, and just loads itself and sits there (synchronizing clock with ntp.ubuntulinux.org fails, due to no DNS activity).

There is no eth0 created when I run /sbin/ifconfig to take a look at the available devices.

However, if I rmmod it once the machine has started up, and reload it again, it detects the hardware and works -- however I have to run dhclient and ifup and such and that's a pain in the ass.

Is there a known issue why it doesn't detect on startup with hotplug and friends but works fine once I manually remove the module and reinstall it?

P.S. if it helps, the installer didn't have access to the network because there was no way of loading the sk98lin and nforce drivers (it didn't autodetect). Is there perhaps a package that needed to be installed that didn't get installed?
P.P.S. when modprobing the versions of sk98lin and forcedeth from the Ubuntu 5.04H release they didn't detect the hardware. Same goes for the "official" NVidia nvnet. I upgraded to 8.32 because the version of sk98lin that came on the Asus motherboard CD was too old for Linux 2.6.x

---

### Post by ravuya on 2005-07-13
Quick update:

When I put sk98lin at the top of /etc/modules (i.e. before nvidia) and check dmesg, it detects the eth0 device but ifconfig can't see it. I again have to rmmod and re-install the module in order for it to be "found" by ifconfig.

I will try modifying /etc/network/interfaces and see if that works.

---

### Post by ravuya on 2005-07-13
Yes, it most certainly did!

For future reference:

add the eth0 entry to the "auto" line in /etc/network/interfaces.
add "iface eth0 inet dhcp" to /etc/network/interfaces.

Thanks to the people who tried to help on irc.

---

