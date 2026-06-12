---
title: "Disabling a Driver?"
date: 2009-06-20
forum: Hardware
---

### Post by Benz0r on 2009-06-20
Hello all. I ran into a little problem. On my laptop I was playing around, and I went into the Hardware enabler thing, and enabled my LAN driver, and it took over and now I can't use wireless. Basically all I need is to know how to disable my LAN driver, and let my wireless driver to take control.

Thanks, Benny.

---

### Post by cariboo on 2009-06-20
You didn't say what version you are using, but normally to stop a driver from loading, you add it to for Intrepid /etc/modprobe.d/blacklist, or for Jaunty /etc/modprobe.d/blacklist.conf.

To edit the file press Alt-F2 and type:

```
gksu gedit /etc/modprobe.d/blacklist
``` or blacklist.conf.

If you're not sure which driver it is open an Applications-->Accessories-->Terminal and type:

```
sud lshw -C network
```

the results will look something like this:

```
*-bridge
       description: Ethernet interface
       product: MCP51 Ethernet Controller
       vendor: nVidia Corporation
       physical id: 14
       bus info: pci@0000:00:14.0
       logical name: eth0
       version: a3
       serial: 00:16:17:9c:84:b5
       size: 100000000
       capacity: 1000000000
       width: 32 bits
       clock: 66MHz
       capabilities: bridge pm bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes **driver=forcedeth** driverversion=0.64 duplex=full ip=192.168.1.100 latency=0 link=yes maxlatency=20 mingnt=1 module=forcedeth multicast=yes port=MII speed=100MB/s
```

For some reason the kernel sees my network device as a bridge device. I have bolded the driver part of the output, in my case it is the forcedeth driver, yours will be different.

---

