---
title: "Need help getting Network Controller driver's installed on older distro"
date: 2023-04-18
forum: Hardware
---

### Post by mrjanuary on 2023-04-18
Hello, I recently got a new Dell here is [lshw dump]("https://paste.gloriouseggroll.tv/?b4f74ad89d369f10#F8LfMqcex7f23FKeVB8AjJJeHtNaJJ1uuJBXgaNvtavZ"). I need to get ubuntu 18.04 up and running on this hardware. Currently, I have it running with a dual boot setup. However, 18.04 is unable to recognize the Network Controller e.g. ```
lshw -C network
``` show's two unclaimed networks. Obviously, 22.04 has the correct drivers for the controller. Is it possible for me to transfer the drivers from this 22.04 installation onto that 18.04 installation? Perhaps I could download the drivers onto a usb and move them that way?

---

### Post by TheFu on 2023-04-18
Drivers are per kernel version, so no, you can't transfer/copy them over.

Please post the network parts of the lshw output here. Don't make it hard for people to help you, please. I won't be clicking on some external link when 10 lines of text posted here would be fine. No clickbait, please.

BTW, standard support for 18.04 ends shortly - like in less than a month - so nobody should be dealing with 18.04 stuff anymore at this point ... nor since about a year ago.  It is time better spent using 20.04 or getting 22.04 working.

---

### Post by mrjanuary on 2023-04-18
If only my boss's agreed with you. Apparently, they don't see the value in spending "10's of thousands" of dollars in development time upgrading when 18.04 works fine for the platform. In any case, here is the relevant portions of the lshw dump: 

```
robert@bznlinux050:~$ lshw
...
        *-network:0 UNCLAIMED
             description: Network controller
             product: Intel Corporation
             vendor: Intel Corporation
             physical id: 14.3
             bus info: pci@0000:00:14.3
             version: 11
             width: 64 bits
             clock: 33MHz
             capabilities: cap_list
             configuration: latency=0
             resources: iomemory:600-5ff memory:6001134000-6001137fff
...
        *-network:1 UNCLAIMED
             description: Ethernet controller
             product: Intel Corporation
             vendor: Intel Corporation
             physical id: 1f.6
             bus info: pci@0000:00:1f.6
             version: 11
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: latency=0
             resources: memory:70500000-7051ffff
  *-network
       description: Ethernet interface
       physical id: 1
       logical name: enp0s20f0u1
       serial: 4a:cf:76:96:4f:11
       capabilities: ethernet physical
       configuration: broadcast=yes driver=rndis_host driverversion=22-Aug-2005 firmware=RNDIS device ip=192.168.101.133 link=yes multicast=yes
```

I would note, since my original post I have managed to get internet on the PC using a usb tether between it and my phone. I am currently on the 18.04 distro now.

---

### Post by TheFu on 2023-04-18
Thanks for the code tags.

"Intel Corporation" is pretty generic.  The specific model is needed ... and if you can boot (use a Flash drive in a "Try Ubuntu" mode) to get the information with 22.04, we'd be able to see the driver being used.

lshw is a great tool, but perhaps this NIC is too new for the 4.xx kernel?  Have you tried moving the system to the 5.4.x kernel using HWE?  Other ways to get the NIC model and driver are:
```
lspci -vk |perl -lne 'print if /Ethernet|Network/ .. /^[\w]*$/' 
inxi -Nxxz
```

For example, 
```
$ inxi  -Nxx
Network:   Card: Intel I211 Gigabit Network Connection
           driver: igb v: 5.6.0-k port: d000
           bus-ID: 03:00.0 chip-ID: 8086:1539

$ inxi  -Nxx
Network:   Device-1: Intel I211 Gigabit Network vendor: ASUSTeK driver: igb v: kernel port: d000 bus ID: 03:00.0 
           chip ID: 8086:1539 
           Device-2: Intel 82575GB Gigabit Network driver: igb v: kernel port: c020 bus ID: 07:00.0 
           chip ID: 8086:10d6 
           Device-3: Intel 82575GB Gigabit Network driver: igb v: kernel port: c000 bus ID: 07:00.1 
           chip ID: 8086:10d6 
           Device-4: Intel 82575GB Gigabit Network driver: igb v: kernel port: b020 bus ID: 08:00.0 
           chip ID: 8086:10d6 
           Device-5: Intel 82575GB Gigabit Network driver: igb v: kernel port: b000 bus ID: 08:00.1 
           chip ID: 8086:10d6 

# the other lspci command will kick out something like this:
$ lspci -vk |perl -lne 'print if /Ethernet|Network/ .. /^[\w]*$/' 
03:00.0 Ethernet controller: **Intel Corporation I211 Gigabit** Network Connection (rev 03)
        Subsystem: ASUSTeK Computer Inc. I211 Gigabit Network Connection
        Flags: bus master, fast devsel, latency 0, IRQ 32
        Memory at fc800000 (32-bit, non-prefetchable) [size=128K]
        I/O ports at d000 [size=32]
        Memory at fc820000 (32-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>
        Kernel driver in use: igb
        **Kernel modules: igb**

08:00.1 Ethernet controller: Intel Corporation **82575GB** Gigabit Network Connection (rev 02)
        Subsystem: Intel Corporation Gigabit VT Quad Port Server Adapter
        Flags: bus master, fast devsel, latency 0, IRQ 34
        Memory at fc000000 (32-bit, non-prefetchable) [size=128K]
        Memory at fbc00000 (32-bit, non-prefetchable) [size=2M]
        I/O ports at b000 [disabled] [size=32]
        Memory at fc040000 (32-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>
        Kernel driver in use: igb
        **Kernel modules: igb**

```

My 22.04 box used the 5.15.x kernels.

As for running an unsupported release, your immediate boss may not have the authority to agree to do that. 

Generally, it takes a corporate officer to accept risks like that, since corporate insurance is usually voided when running unsupported OSes.  I've had to write up a number of "Risk Acceptance" letters to be signed by corporate officers in my $day_job.  

Every single time, they asked what it would take to correct and wanted a plan by all the involved teams to work towards that solution.  Nullifying a $1M - $200M corporate insurance policy over $50K in effort is bad business, especially if the officers didn't know about the risk at all.  I promise you, the insurance company will ask and if every system isn't on a supported OS, that's reason enough to void the policy.  They don't give refunds.

Anyway, the paperwork also protects you from being fired because the letter would provide a paper trail that you told someone and tried to get it addressed. The trick is getting it in front of the right people.  

I've had meetings with a CIO of a Fortune 10 company about risk letters and meetings with a tiny client that had 3 people working for him. Running unsupported OSes isn't an option in a business.

---

### Post by mrjanuary on 2023-04-18
I manged to update too 5.15.0-69-generic by accessing the 20.x repository. That has allowed me access to an Ethernet driver so I am not having to use my phone anymore XD. Still no wifi. There are a few other drivers that seem to be missing as well. Including one for the RAM? Not sure how I am using the OS at all with no driver for the RAM...

---

### Post by TheFu on 2023-04-19
Since the requested commands haven't been run, I assume this thread is SOLVED.  Congratulations.

---

