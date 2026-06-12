---
title: "RAM recognized in BIOS and in Lubuntu 18.10, but not available for use."
date: 2019-04-01
forum: Hardware
---

### Post by finnegantimothyd98 on 2019-04-01
Hey there!

I'm running Lubuntu 18.10 on an old Dell Dimension E510 Desktop Computer.

I've installed 6 gigabytes of DDR2 RAM into the machine, two 1 GB sticks and two 2 GB sticks.

The BIOS recognizes all of the RAM, as does Lubuntu.

The operating system does not seem to want to give me full access to all of my RAM, however.

Here's the output of ```
 sudo lshw - class memory 
```

```

tim@tim-pc:~$ sudo lshw -class memory
  *-firmware                
       description: BIOS
       vendor: Dell Inc.
       physical id: 0
       version: A05
       date: 03/31/2006
       size: 64KiB
       capacity: 448KiB
       capabilities: pci pnp apm upgrade shadowing cdboot bootselect edd int13floppytoshiba int5printscreen int9keyboard int14serial int17printer acpi usb ls120boot biosbootspecification netboot
  *-cache:0
       description: L1 cache
       physical id: 700
       size: 16KiB
       capacity: 16KiB
       capabilities: internal write-back data
       configuration: level=1
  *-cache:1
       description: L2 cache
       physical id: 701
       size: 2MiB
       capacity: 2MiB
       capabilities: internal varies unified
       configuration: level=2
  *-memory
       description: System Memory
       physical id: 1000
       slot: System board or motherboard
       size: 6GiB
     *-bank:0
          description: DIMM DDR Synchronous 533 MHz (1.9 ns)
          product: VS1GB667D2
          vendor: 7F7F9E0000000000
          physical id: 0
          serial: 00000000
          slot: DIMM_1
          size: 1GiB
          width: 64 bits
          clock: 533MHz (1.9ns)
     *-bank:1
          description: DIMM DDR Synchronous 533 MHz (1.9 ns)
          product: V02D2LF2GB1881880
          vendor: 0000000000000000
          physical id: 1
          serial: 00000000
          slot: DIMM_3
          size: 2GiB
          width: 64 bits
          clock: 533MHz (1.9ns)
     *-bank:2
          description: DIMM DDR Synchronous 533 MHz (1.9 ns)
          product: V02D2LF2GB1881880
          vendor: 0000000000000000
          physical id: 2
          serial: 00000000
          slot: DIMM_2
          size: 2GiB
          width: 64 bits
          clock: 533MHz (1.9ns)
     *-bank:3
          description: DIMM DDR Synchronous 533 MHz (1.9 ns)
          product: VS1GB667D2
          vendor: 7F7F9E0000000000
          physical id: 3
          serial: 00000000
          slot: DIMM_4
          size: 1GiB
          width: 64 bits
          clock: 533MHz (1.9ns)

```

I am running 64-bit lubuntu
```

tim@tim-pc:~$ uname -m
x86_64
 
```


So I have a 64-bit version of the machine, the BIOS detects all 64 gigabytes of RAM, and Ubuntu can see all four RAM chips.

When I run ```
 free -m 
```, I get:

```

tim@tim-pc:~$ free -m
total        used        free      shared  buff/cache   available
Mem:           3629        2108         632          23         888        1322

```(The machine has Swap space, I just excluded that here)

However, when I run the command htop, it shows that I only have 3.54G of RAM, and when I run a .jar file in Java with a maximum and minimum amount of 4GB of RAM usage -- Beyond what htop is showing --, it crashes the machine.
[IMG]https://i.imgur.com/WlgCjmP.png[/IMG]

Other than the change in memory, the machine is otherwise entirely stock.

Could somebody help me figure out what I'm missing, here? I've tried installing different ram chips, reseating the ram, changing the ports that the different ram chips are installed in and so on, and I have seen no change in the outputs to these commands.

---

### Post by Yellow Pasque on 2019-04-03
Dell states the maximum memory of the e510 is 4GB, meaning the BIOS/chipset probably does not support the necessary memory remapping/hoisting to take advantage of RAM beyond that. Even if the RAM is physically recognized and you can boot an OS, that doesn't mean memory above 4GB is addressable.

I hope you can return the 2GB memory modules or you just lost some money and learned a lesson the hard way.

---

