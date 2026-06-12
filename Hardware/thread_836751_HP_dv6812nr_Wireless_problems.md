---
title: "HP dv6812nr Wireless problems"
date: 2008-06-21
forum: Hardware
---

### Post by jazee on 2008-06-21
I am having problems getting the wireless interface to be seen in Network Manage or anywhere else. 

I have install the b43-fwcutter driver as suggested here: [https://wiki.ubuntu.com/HP_dv6000_Series#head-620e0d4896ac78e30bde75792dc1ccaf3e2c79ba](https://wiki.ubuntu.com/HP_dv6000_Series#head-620e0d4896ac78e30bde75792dc1ccaf3e2c79ba)
Which as you can tell didn't do anything. 

I am also showing in the Proprietary drivers window 2 driver that are being used besides the NVidia driver. "Atheros Hardware Access Layer(Hal)" Not sure what that one is but I am also showing one that seems like it should be helping out. "Support for Artheros 802.11 wireless LAN cards"

Any idea of how to get this to work?

---

### Post by cwbar_1 on 2008-06-22
When you installed b43-fwcutter, did it ask you "fetch and install driver"? If not, reinstall using synaptic.  (choose the fwcutter with the Ubuntu logo next to it)

---

### Post by jazee on 2008-06-22
I reinstalled the driver from a complete remove just to make sure that that option was checked and still no change. ifconfig -a shows only the loopback and the 10/100 port.

---

### Post by cwbar_1 on 2008-06-22
OK. Let's go back to basics.  Please post the output of lspci.

---

### Post by jazee on 2008-06-22
Here is the network portion of both lspci & lshw

```

%lspci

03:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)

```

```

%sudo lshw

*-network UNCLAIMED
             description: Ethernet controller
             product: AR242x 802.11abg Wireless PCI Express Adapter
             vendor: Atheros Communications Inc.
             physical id: 0
             bus info: pci@0000:03:00.0
             version: 01
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi pciexpress msix cap_list
             configuration: latency=0


```

---

### Post by jazee on 2008-06-22
I tried 2 of the solution on this thread as well. both seem to have not worked for me. [http://ubuntuforums.org/showthread.php?t=766169](http://ubuntuforums.org/showthread.php?t=766169)

---

### Post by cwbar_1 on 2008-06-23
After a little more research, it seems that this card _may_ be reported incorrectly by Hardy. See [https://bugs.launchpad.net/ubuntu/+bug/209414](https://bugs.launchpad.net/ubuntu/+bug/209414) 
Can you use another operating system, aka another live CD, to check the correctness of the detected card?  If so, you may be able to get it to work by installing the correct driver.  See also the last post of [http://www.linuxquestions.org/questions/linux-laptop-and-handheld-25/wireless-wont-work-atheros-ar242x-802.11abg-646443/](http://www.linuxquestions.org/questions/linux-laptop-and-handheld-25/wireless-wont-work-atheros-ar242x-802.11abg-646443/)
Reply back and if I can't help, I'm sure someone else can.  Stick with it!

---

### Post by jazee on 2008-06-24
Thanks, The Launchpad bug you listed had the link to the duplicate bug that worked for solving the problem. [https://bugs.edge.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.24/+bug/182489](https://bugs.edge.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.24/+bug/182489)

I ended up needing to remove ndiswrapper and all its modules. Then had to hand compile the current trunk of madwifi with the most recent HAL release.

---

### Post by lincoln2tg on 2009-09-10
Hello everybody

I got a new [[COLOR=#2a4d66]hp dv6000 battery[/COLOR]]("http://www.8eshop.com/laptop-battery/hp-pavilion-dv6000-battery.htm") for my notebook and the next day I can't use my wifi, I don't know whether the battery have a fault or other thing went wrong, the battery is a 12 cell high capacity one.

---

