---
title: "Refreshing your Ethernet Adapter Driver"
date: 2007-09-28
forum: Hardware &amp; Laptops
---

### Post by abrichr on 2007-09-28
Hey all, I thought I might post this information simply in the spirit of sharing the wealth of knowledge.  Please post if you find this information incorrect or incomplete.

I find it very annoying that if you don't start Ubuntu with your Ethernet device activated, Ubuntu won't automatically enable the driver when you activate it.  For example, if your Ethernet cable isn't plugged in to your adapter or if your wireless switch isn't on while booting up, then Ubuntu won't see them acquire an IP address once you plug the Ethernet cord in/turn on the wireless switch.

I did some hunting around, and finally figured out how to do this.

First, you'll need to find out the name of the interface through which you're connecting.  Open up a terminal, and type:

```
ifconfig
```

ifconfig displays all known network interfaces.  If this command only outputs "lo", you'll need to install the correct driver for your network device.  lo is the name of the loopback interface, which is simply a connection to the IP 127.0.0.1, which references your own machine.

Most likely, the name of your wired network controller is eth0, and the name of your wireless network controller (if you have one) is eth1.  You may also see eth0:avah and/or eth1:avah.  This indicates that avahi is running for that device.  Avahi is the service that allows facilitates the discovery of services on a network, such a DHCP server, from which to acquire an IP address.

If you don't see this, then your network card will most likely not be able to acquire an IP, particularly if you're dependent on DHCP.  If you've booted up without your network interface activated, and are unable to connect, type:

```
sudo ifconfig [device-id] up
```

Remember to replace [device-id] with the name of the device you wish to activate.

And there you have it.  Too bad Canonical didn't include this as a feature in the Network Settings GUI.  In any case, if you want more information about ifconfig, type

```
man ifconfig
```

into the terminal, or visit [http://www.avahi.org/](http://www.avahi.org/) for information and documentation about avahi.

---

