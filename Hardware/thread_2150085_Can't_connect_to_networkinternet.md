---
title: "Can't connect to network/internet"
date: 2013-05-30
forum: Hardware
---

### Post by jankonia on 2013-05-30
I am rebuilding a computer after my ASRock 990FX Extreme4 Mobo crapped out on me.  After having this failure I decided to use a different Mobo in hopes of avoiding a similar situation.  I ordered a GIGABYTE 990FXA-UD3 rev.3 and got the sucker in and booting without issue, that is until I tried to connect to the network.  This is a home build so it is not a problem with my network, I know that for sure.  I have tried downloading and installing new network drivers, but this integrated card doesn't seem to play well with Ubuntu.  I am trying the newest distro of 13.04, 12.10, OR 12.04.  

In hopes of throwing money at the problem I bought an Intel Pro 1000 GT NIC, but I have been unsuccessful with this as well.

After screwing around with the integrated and PCI NICs above I got desperate and threw a little more money at the problem and ordered a Rosewill Gigabit LAN PCI Adapter as well.  From the looks of it the Rosewill and integrated NICs have the same Realtek Chipsets =/.

So far none of these NICs have been able to connect to my network let alone the internet, please help me!

I know the current install of 12.04 that I am working with is kernel 3.5.x.  When I try to build the drivers for any of these cards they fail as they are written for 2.6.x and older.  Intel notes on their page that the driver support is kernel based now.  This is all a little over my head and I need help to get this computer up and running again.

Links to the pages of the hardware I am working with:
MOBO: [http://www.gigabyte.us/products/product-page.aspx?pid=4397#ov](http://www.gigabyte.us/products/product-page.aspx?pid=4397#ov)
NIC 1: [http://ark.intel.com/products/50480/Intel-PRO1000-GT-Desktop-Adapter](http://ark.intel.com/products/50480/Intel-PRO1000-GT-Desktop-Adapter)
NIC 2: [http://www.rosewill.com/products/425/ProductDetail_Overview.htm](http://www.rosewill.com/products/425/ProductDetail_Overview.htm)

I have nothing installed on this computer so I am happy to try anything to get this working so long as I can use 12.04 or newer =)


Thanks!

---

### Post by ahallubuntu on 2013-05-30
I've installed Ubuntu 12.04 on numerous computers, and the wired network card was recognized automatically on all of them (two were Sandy Bridge, the rest were older).  So I guess you've had bad luck!  Or, it's not a matter of the driver at all.

First of all: what's the output of these commands

```
sudo lshw -C network
ifconfig
```

?

Is it a standard network where you are simply connected to a router that uses DHCP to supply an IP address automatically?

---

### Post by jankonia on 2013-06-14
> **ahallubuntu said:**
> I've installed Ubuntu 12.04 on numerous computers, and the wired network card was recognized automatically on all of them (two were Sandy Bridge, the rest were older).  So I guess you've had bad luck!  Or, it's not a matter of the driver at all.

First of all: what's the output of these commands

```
sudo lshw -C network
ifconfig
```

?

Is it a standard network where you are simply connected to a router that uses DHCP to supply an IP address automatically?


This is an AMD AM3+ mobo and CPU (1090T) so maybe that is the difference, I'll add the output from those commands as soon as I can.  I am running a standard home network with a Netgear router that this computer is plugged directly into.  The router is pretty much straight out of the box, just changed the password =)

---

