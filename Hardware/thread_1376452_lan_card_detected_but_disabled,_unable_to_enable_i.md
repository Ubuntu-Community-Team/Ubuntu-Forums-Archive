---
title: "lan card detected but disabled, unable to enable it"
date: 2010-01-09
forum: Hardware
---

### Post by khizar on 2010-01-09
ok so i have got jaunty on my pc and everything was working f9 until yesterday. i m working on my final year project n had to connnect another pc to mine. i had an 'intel 82557/8/9/0/1 ethernet pro 100' ethernet controller so i plugged it in my pc to connect it to the other pc via a cross crimped lan wire. now the problem is i cant get it to work , i mean it is detected by ubuntu but cant be enabled. ifconfig doesnt show it but lshw -C Network gives

```

 *-network:0 DISABLED    
       description: Ethernet interface
       product: 82557/8/9/0/1 Ethernet Pro 100
       vendor: Intel Corporation
       physical id: 1
       bus info: pci@0000:01:01.0
       logical name: eth3
       version: 08
       serial: 00:03:47:ad:53:4b
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=e100 driverversion=3.5.23-k6-NAPI firmware=N/A latency=32 maxlatency=48 mingnt=8 module=e100 multicast=yes
  *-network:1
       description: Ethernet interface
       product: 82562EZ 10/100 Ethernet Controller
       vendor: Intel Corporation
       physical id: 8
       bus info: pci@0000:01:08.0
       logical name: eth0
       version: 01
       serial: 00:16:76:09:44:15
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=e100 driverversion=3.5.23-k6-NAPI firmware=N/A ip=192.168.33.70 latency=32 maxlatency=56 mingnt=8 module=e100 multicast=yes
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 5a:88:9d:7c:fd:43
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes


```

notice the network 0 that is disabled , now i have tried to enable it but to no avail.... 

```

khizar@khizar-desktop:~$ sudo ifconfig eth3 up
[sudo] password for khizar: 
SIOCSIFFLAGS: Connection timed out

```

help me guys coz i need to get this done as soon as possible so i can start work ..... plzzz plzzz plzzz

regards 
khizar

---

### Post by derekmbarnes on 2010-01-09
Try this:

```
lspci -v | less
```

Scroll down to your ethernet controller (or network controller if you're using wireless) near or at the bottom of the list; if the driver is missing, the driver line in the description will be absent. In which you'll need to note down the brand and device number of your card and find a driver for it to get it working again.

---

### Post by khizar on 2010-01-10
thanks for the reply...

i ran the command n hres the output for the two ethernet controllers , the first is the one i cant get to work while the second one is the one currenty in use ..... 
```

01:01.0 Ethernet controller: Intel Corporation 82557/8/9/0/1 Ethernet Pro 100 (rev 08)
        Subsystem: Intel Corporation Device 000b
        Flags: bus master, medium devsel, latency 32, IRQ 22
        Memory at ff800000 (32-bit, non-prefetchable) [size=4K]
        I/O ports at b800 [size=64]
        Memory at ff700000 (32-bit, non-prefetchable) [size=1M]
        Expansion ROM at 20000000 [disabled] [size=1M]
        Capabilities: <access denied>
        Kernel driver in use: e100
        Kernel modules: e100, eepro100

01:08.0 Ethernet controller: Intel Corporation 82562EZ 10/100 Ethernet Controller (rev 01)
        Subsystem: Intel Corporation Device 304a
        Flags: bus master, medium devsel, latency 32, IRQ 20
        Memory at ff901000 (32-bit, non-prefetchable) [size=4K]
        I/O ports at ac00 [size=64]
        Capabilities: <access denied>
        Kernel driver in use: e100
        Kernel modules: e100, eepro100


```

seems like they both have drivers installed ..... thr doesnt seem anything wrong with em n yet one is working n one is not.....

---

