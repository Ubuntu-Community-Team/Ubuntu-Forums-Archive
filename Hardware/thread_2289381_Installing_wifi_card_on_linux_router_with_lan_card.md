---
title: "Installing wifi card on linux router with lan card"
date: 2015-08-03
forum: Hardware
---

### Post by andrew.robbins.fli on 2015-08-03
Hi all,

I have a linux router that I'm running with Ubuntu server. It does DHCP,DNS,ftp, fns, etc. I have had it running only as a lan network and want to add wireless capabilities, so that I have wired a wireless network issuing IP's in the same range. i am not trying to create two separate subnets, rather I want the eth1 and wlan0 interfaces to be linked. I tried to setup the network using the routers page on wired and wireless([https://help.ubuntu.com/community/Router](https://help.ubuntu.com/community/Router)), but the config file when applied does nothing, but bring down my eth1 interface.

Here is the interface configuration that I want:
eth0 is dhcp assignment and is my wan interface
eth1 and wlan0 are static and are the interfaces that the server services outputted on.

Note: I'm running Ubuntu Server 14.04LTS with a webmin GUI interface

Any ideas how the interfaces file should be ammended?

-Andrew

---

