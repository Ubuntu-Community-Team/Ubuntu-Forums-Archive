---
title: "D-Link DWL-G650+ Driver"
date: 2010-10-31
forum: Hardware
---

### Post by joe_mortlock on 2010-10-31
I need help installing my G650+ wireless adapter in 10.10 because all the tutorials are back in 2006/07. Please help me.

---

### Post by P4man on 2010-10-31
The reason you dont find anything more recent is because you dont need drivers anymore, it should work out of the box. Make sure you have enabled wireless networking (right click network manager icon), and that have not disabled wifi with a hardware switch or keycombo.

---

### Post by joe_mortlock on 2010-11-06
Still doesn't work :( Any other ideas?

---

### Post by P4man on 2010-11-06
please post the output of these 3 commands

```
lshw -C network
``` (note UPPERCASE C).
```
iwconfig
```
```
sudo rfkill -list
```

(I am assuming you have a temporarily wired connection so you can copy paste the output. if not, let me know ill explain how to redirect the output to a USB stick).

---

### Post by joe_mortlock on 2010-11-06
1st Code :
  *-network               
       description: Ethernet interface
       product: VT6102 [Rhine-II]
       vendor: VIA Technologies, Inc.
       physical id: 12
       bus info: pci@0000:00:12.0
       logical name: eth0
       version: 74
       serial: 00:c0:9f:3b:30:54
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=via-rhine driverversion=1.4.3 ip=192.168.1.77 latency=64 maxlatency=8 mingnt=3 multicast=yes
       resources: irq:4 ioport:1800(size=256) memory:d0004c00-d0004cff
  *-network UNCLAIMED
       description: Network controller
       product: ACX 111 54Mbps Wireless Interface
       vendor: Texas Instruments
       physical id: 0
       bus info: pci@0000:02:00.0
       version: 00
       width: 32 bits
       clock: 33MHz
       capabilities: cap_list
       configuration: latency=0
       resources: memory:24020000-24021fff memory:24000000-2401ffff

2nd Code:
lo        no wireless extensions.

eth0      no wireless extensions.

3rd Code:
Usage:    rfkill [options] command
Options:
    --version    show version (0.4)
Commands:
    help
    event
    list [IDENTIFIER]
    block IDENTIFIER
    unblock IDENTIFIER
where IDENTIFIER is the index no. of an rfkill switch or one of:
    <idx> all wifi wlan bluetooth uwb ultrawideband wimax wwan gps fm

That it???

---

### Post by P4man on 2010-11-06
Oh, its an ACX 111 chipset. well, no support for that in the kernel and in fact, no usable native drivers afaik. Sorry I thought it used a different chipset.

Your best/only option is probably ndiswrapper:

[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)

---

