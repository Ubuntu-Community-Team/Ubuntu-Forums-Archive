---
title: "No network after server restart"
date: 2018-11-09
forum: Hardware
---

### Post by dai-webb on 2018-11-09
Hello.

I have a virtual (VMware) server running Ubuntu Server 18.04 which has been working perfectly for months. Today the server got restarted and now has no network connectivity.

The NIC is configured in /etc/network/interfaces:

[FONT=courier new]auto ens160
iface ens160 inet static
address 192.168.0.100
netmask 255.255.255.0
gateway 192.168.0.254
dns-nameservers 192.168.0.102[/FONT]

When I run "lshw -C network" it shows the network as disabled.  I can enable this using "ifconfig ens160 up" but still nothing (can't ping in or out).  Pinging out says "Connect: Network is unreachable".

I have tried disabling the firewall using "ufw disable" and still nothing

I have tried setting the interface to DHCP but it doesn't get an address.

I have checked the VM settings in vCenter and it's all correct.

Running "ifconfig -a" lists the interface ens160 but doesn't list an inet address or mask.

Running "dmesg | grep ens160" just shows some firewall blocks but I've disabled that now.

Where can I start looking next to fix this please?  I'm not much of a Linux buff I'm afraid.

---

### Post by dai-webb on 2018-11-09
I managed to fix this by running "[FONT=monospace]systemctl restart systemd-networkd".  However, the problem returned after restarting the server again.  Why would I need to run this each time I restart the server just to get networking working?[/FONT]

---

