---
title: "Installing 8.10 Desktop with a static IP address"
date: 2008-12-22
forum: Installation &amp; Upgrades
---

### Post by dant262 on 2008-12-22
I'm new to Ubuntu, but have used various other Linux implementations for some time.  I'm trying to install the Desktop version of Ubuntu 8.10, but to use a static IP address rather than a DHCP-assigned one.

I can do this easily with Server and Alternate, by entering a boot parameter (netcfg/disable_dhcp=true), but don't seem to be able to get this to work with Desktop.

When I try the boot parameter, it still does not ask me to enter static IP information during the install, and, if I edit this (IPv4) information in "System | Preferences | Network Configuration" (or by RClicking on the "Wired Network Connections" icon and selecting "Edit Connections") the settings are activated *until I reboot the machine*.  Then they are lost...

I'd like to see how to do this *through the GUI* rather than by manually editing the /etc/network/interfaces file... (I can do it that way, but am teaching students about Linux and, at least for this point in the process, would like to have them use the GUI...)

I'm wondering if someone can help me with the proper way to accomplish permanently setting these IP settings.

Thanks ahead of time,

dant262

---

### Post by Aulendil on 2009-01-21
Hello dant262

I have had the same problem with Ubuntu 8.10 desktop. It looks like that there is a bug in the Gnome Network Manager. Just uninstall the network manager and edit the configuration files yourself.

```

sudo apt-get remove –purge network-manager

sudo vi /etc/network/interfaces

[I]
auto eth0
iface eth0 inet static
address 192.168.1.11
netmask 255.255.255.0
gateway 192.168.1.1
[/I]

sudo vi /etc/resolv.conf

[I]
nameserver 208.67.222.222
nameserver 208.67.220.220
[/I]

sudo /etc/init.d/networking restart

```

Aulendil

---

