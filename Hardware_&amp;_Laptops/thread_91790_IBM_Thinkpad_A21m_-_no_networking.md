---
title: "IBM Thinkpad A21m - no networking"
date: 2005-11-18
forum: Hardware &amp; Laptops
---

### Post by bribera on 2005-11-18
Hi there-

I recently installed Breezy Badger on my Thinkpad A21m.  Hardware detection went perfectly, except for the network interfaces.

Neither of the networking options I have were detected, and as such, neither are working:
1 built-in port
1 Wifi card (Orinoco 802.11b Silver)

I'm a little surprised that I got *no* network devices detected whatsoever, as they're both pretty old.  Any suggestions as to how I can get them working?

---

### Post by Lambert on 2005-11-18
Can you post the outputs of 

ifconfig
iwconfig
sudo lshw -C network

Are you running dhcp or static ip addressing?
Are you running encryption, if yes then wep or wpa

You didn't say so I have to ask. Did you go into system>admin>networking and try to set up and activate?

---

### Post by bribera on 2005-11-18
Well, I'm not at home with the comp. right now, but here's what I know:

ifconfig shows only lo  (see, my NIC isn't even coming up as eth0)
iwconfig shows lo and sit0, both with no wireless extensions

I'm unsure about lshw; I'll post that sometime tomorrow.


Ubuntu failed to detect my NIC during installation; I tried running the latest Debian install, and it detected it.  That seems pretty weird to me... I really like Ubuntu, but it may be easier to just install plain ol' Debian.

---

### Post by Lambert on 2005-11-18
Here's a copy of my lshw for my ethernet card

*-network DISABLED
       description: Ethernet interface
       **product: 82801CAM (ICH3) PRO/100 VE (LOM) Ethernet Controller**
       vendor: Intel Corporation
       physical id: 8
       bus info: pci@02:08.0
       logical name: eth0
       version: 42
       serial: 00:02:8a:29:46:9c
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegociation
       configuration: autonegociation=on broadcast=yes **driver=e100 driverversion=3.4.8-k2-NAPI** duplex=half firmware=N/A link=no multicast=yes port=MII speed=10MB/s
       resources: iomemory:d0200000-d0200fff ioport:8000-803f irq:11

What I'm looking for is the driver that's loaded for the device or the make of it to see what driver is recommended. In your case there isn't one loaded with it not showing in ifconfig. If/When you load debian back on you can run this same command. i'd be curious what driver is being loaded there and not in ubuntu.

otherwise post back your lshw.

It looks like your wireless device uses the wavelan driver which is part of breezy.

/lib/modules/2.6.12-9-386/kernel/drivers/net/wireless/wavelan.ko

When you run lshw look for your wireless device to see what driver is shown for that.

If it shows wavelan then 

lsmod | grep wav

and see if it's loaded.

---

### Post by bribera on 2005-11-19
Here's the lshw output:
```
sudo lshw -C network
WARNING: you should run this program as super-user.
  *-network UNCLAIMED
     description: Ethernet controller
     product: 3c556B CardBus [Tornado]
     vendor: 3Com Corporation
     physical id: 3
     bus info: pci@00:03.0
     version: 20
     width: 32 bits
     clock: 33MHz
     capabilities: cap_list
     resources: ioport:1800-18ff iomemory:f4101400-f410147f
iomemory:f4101000-f410107f irq:11
```

Update:

Starting the installer with "linux acpi=off" detects my built-in card.  Still nothing on my wireless.

---

### Post by autek on 2005-11-19
Try 

thinkwiki.org


All IBM Thinkpads and quite a bit of useful info. Including how to get wireless 3com working under Linux.

Ed

---

### Post by autek on 2005-11-19
Also you might have to install the Oronco card with ndiswrapper.

Ed

---

### Post by bribera on 2005-11-20
After doing the install with acpi=off, lshw gives the following:
```
sudo lshw -C network
  *-network
       description: Wireless PC Card Model 0110
       vendor: Agere Systems
       physical id: 0
       slot: Socket 1
  *-network
       description: Ethernet interface
       product: 3c556B CardBus [Tornado]
       vendor: 3Com Corporation
       physical id: 3
       bus info: pci@00:03.0
       logical name: eth0
       version: 20
       serial: 00:01:03:83:12:bc
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegociation
       configuration: autonegociation=on broadcast=yes driver=3c59x driverversion=LK1.1.19 duplex=full ip=192.168.0.2 link=yes multicast=yes port=MII speed=100MB/s
       resources: ioport:1800-18ff iomemory:f4101400-f410147f iomemory:f4101000-f410107f irq:11
```

So, it sees the card.  iwconfig still shows 0 wireless extensions.  I'm going to look into ndiswrapper.

---

### Post by bribera on 2005-11-21
thinkwiki.org's explanation of the ethernet driver problem made me wonder if it might be beneficial to install using the most recent kernel - apparently, the ethernet won't be detected unless one uses acpi=off or if one uses 2.6.14-rc1/newer.

So, my question now is:

What does installing with acpi=off do?  Is it detrimental, or should I not worry about it?
Is there a way to turn it back on after compiling the latest kernel? or to compile a new kernel and run the installation process using that kernel?

EDIT: also, what kernel does dapper drake come with?  Might as well just download that and see if it has the fixed version.

---

