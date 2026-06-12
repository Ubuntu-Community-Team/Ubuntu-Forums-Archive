---
title: "ifplugd doesn't work at boot, still searching for network"
date: 2005-11-26
forum: General Help
---

### Post by Zym0tiC on 2005-11-26
At boot my laptop waits when searching for a network. Normally I solved this by installing ifplugd and configured eth0 for this. But after a reinstall it doesn't work anymore.

After I get into ubuntu I plug in my network cable and a tail -f /var/log/syslog shows the following:

Nov 26 21:29:19 localhost ifplugd(eth0)[7008]: Link beat detected.
Nov 26 21:29:20 localhost ifplugd(eth0)[7008]: Executing '/etc/ifplugd/ifplugd.action eth0 up'.
Nov 26 21:29:20 localhost ifplugd(eth0)[7008]: client: /sbin/ifup: interface eth0 already configured
Nov 26 21:29:20 localhost ifplugd(eth0)[7008]: Program executed successfully.

How to solve this?

after this I tried:
sudo update-rc.d -f hotplug-net remove

but when I reboot it still wants to discover network

my /etc/network/interfaces:

# The loopback network interface
auto lo
iface lo inet loopback

# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
mapping hotplug
        script grep
        map eth0

# The primary network interface
iface eth0 inet dhcp

iface ath0 inet dhcp

---

### Post by Zym0tiC on 2005-11-26
I solved it by setting NET_AGENT_POLICY to hotplug in /etc/default/hotplug :)

---

