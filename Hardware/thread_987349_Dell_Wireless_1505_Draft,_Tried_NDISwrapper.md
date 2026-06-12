---
title: "Dell Wireless 1505 Draft, Tried NDISwrapper"
date: 2008-11-19
forum: Hardware
---

### Post by Ajakson on 2008-11-19
I am on a Dell inspiron 1525 with a Dell Wireless 1505 Draft 802.11n WLAN mini-card. I have followed all the steps to NDISwrapper and it has the correct driver.

For some reason, I am not picking up any wireless networks when my Windows partition catches at least 3. Why is this not working?

---

### Post by cariboo on 2008-11-19
To make sure that your wireless device is working, could you paste the output of:

```
sudo lshw -C network
```

In your next post. The above command must be run in a Applications-->Accessories-->Terminal.

Jim

---

### Post by Ajakson on 2008-11-19
$ sudo -C network
sudo: illegal option `-C'
usage: sudo -h | -K | -k | -L | -l | -V | -v
usage: sudo [-bEHPS] [-p prompt] [-u username|#uid] [VAR=value]
            {-i | -s | <command>}
usage: sudo -e [-S] [-p prompt] [-u username|#uid] file ...

---

### Post by Ajakson on 2008-11-20
Sorry, new to linux. mistyped that last command.

Here is "sudo lshw -c network"

  *-network               
       description: Ethernet interface
       product: 88E8040 PCI-E Fast Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: eth0
       version: 12
       serial: 00:21:9b:de:1a:a6
       size: 100MB/s
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.20 duplex=full firmware=N/A ip=10.31.169.89 latency=0 link=yes module=sky2 multicast=yes port=twisted pair speed=100MB/s
  *-network UNCLAIMED
       description: Network controller
       product: BCM4328 802.11a/b/g/n
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0b:00.0
       version: 03
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0

---

### Post by Ajakson on 2008-11-20
Any help out there?

---

### Post by Ajakson on 2008-11-20
Bump.

I need to get this working. Can someone please help?

---

