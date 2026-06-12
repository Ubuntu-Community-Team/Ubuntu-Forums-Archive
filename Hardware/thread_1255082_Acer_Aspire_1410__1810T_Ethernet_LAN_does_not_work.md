---
title: "Acer Aspire 1410 / 1810T Ethernet LAN does not work"
date: 2009-09-01
forum: Hardware
---

### Post by Prikolchik on 2009-09-01
On Ubuntu 9.04 Jaunty Jackalope Ethernet LAN card on Acer Aspire 1410 (aka 1810T) is recognized, but does not work out of the box. To get it to work you have to install the driver from Atheros as suggested by [Homay]("http://kubuntuforums.net/forums/index.php?action=profile;u=35908") over at [Kubuntu forums]("http://kubuntuforums.net/forums/index.php?topic=3105954.0")

[SIZE="3"]Step 1. Make sure you have the correct LAN card.[/SIZE]
```
lspci -nn | grep Ethernet
```
should give
```
01:00.0 Ethernet controller [0200]: Attansic Technology Corp. Device [1969:1063] (rev c0)
```
Windows reports this card as Atheros AR8131 PCI-E Gigabit

[SIZE="3"]Step 2. Download the driver sources.[/SIZE]
Go over to the [Atheros driver page]("http://partner.atheros.com/Drivers.aspx") and download **AR81Family-linux-v1.0.0.10.tar.gz** 

[SIZE="3"]Step 3. Unpack the driver.[/SIZE]
[FONT="Courier New"]cd[/FONT] to where you saved the driver file and type:
```
tar -zxf AR81Family-linux-v1.0.0.10.tar.gz
```
The unpacking process may produce some errors/warnings - simply ignore them. 

[SIZE="3"]Step 4. Compile and install[/SIZE]
```
cd src/
make
sudo make install
```
That is it. Now you can either reboot the machine or type:
```
sudo modprobe atl1e
```
and you LAN card should work!

In case you get stuck there is a README file included with the driver.

Cheers! :)

---

### Post by MRRT on 2009-09-01
I want to thank you.
It really work on my wife's aspire notebook.

---

### Post by juliansuddaby on 2009-09-04
Thanks for this!

---

### Post by brelovich on 2009-09-07
Thanks a bunch!

Works great, with the exception of the driver name. Instead of this:

```
sudo modprobe arl1e

```

I need to do this:

```
sudo modprobe atl1e

```

I don't know if this is a typo or some subtle difference in the hardware. I've got a Swedish Acer 1810T and the output from lspci is exactly the same.

---

### Post by Prikolchik on 2009-09-07
> **brelovich said:**
> Thanks a bunch!

Works great, with the exception of the driver name. Instead of this:

```
sudo modprobe arl1e

```

I need to do this:

```
sudo modprobe atl1e

```

I don't know if this is a typo or some subtle difference in the hardware. I've got a Swedish Acer 1810T and the output from lspci is exactly the same.You are right. I have a typo in my instructions.

---

### Post by mitch_feaster on 2009-10-29
Has anyone tried this in 9.10? When I try to compile the driver I get the following errors:

```
mgalgs@cobalgz:~/src/atheros/src$ make
make -C /lib/modules/2.6.31-14-generic/build SUBDIRS=/home/mgalgs/src/atheros/src modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.31-14-generic'
  CC [M]  /home/mgalgs/src/atheros/src/at_common_main.o
  CC [M]  /home/mgalgs/src/atheros/src/atl1e_main.o
/home/mgalgs/src/atheros/src/atl1e_main.c: In function ‘atl1e_request_irq’:
/home/mgalgs/src/atheros/src/atl1e_main.c:156: warning: passing argument 2 of ‘request_irq’ from incompatible pointer type
include/linux/interrupt.h:116: note: expected ‘irq_handler_t’ but argument is of type ‘void (*)(int,  void *)’
/home/mgalgs/src/atheros/src/atl1e_main.c: In function ‘atl1e_probe’:
/home/mgalgs/src/atheros/src/atl1e_main.c:287: error: ‘struct net_device’ has no member named ‘open’
/home/mgalgs/src/atheros/src/atl1e_main.c:288: error: ‘struct net_device’ has no member named ‘stop’
/home/mgalgs/src/atheros/src/atl1e_main.c:289: error: ‘struct net_device’ has no member named ‘hard_start_xmit’
/home/mgalgs/src/atheros/src/atl1e_main.c:290: error: ‘struct net_device’ has no member named ‘get_stats’
/home/mgalgs/src/atheros/src/atl1e_main.c:291: error: ‘struct net_device’ has no member named ‘set_multicast_list’
/home/mgalgs/src/atheros/src/atl1e_main.c:292: error: ‘struct net_device’ has no member named ‘set_mac_address’
/home/mgalgs/src/atheros/src/atl1e_main.c:293: error: ‘struct net_device’ has no member named ‘change_mtu’
/home/mgalgs/src/atheros/src/atl1e_main.c:294: error: ‘struct net_device’ has no member named ‘do_ioctl’
/home/mgalgs/src/atheros/src/atl1e_main.c:305: error: ‘struct net_device’ has no member named ‘tx_timeout’
/home/mgalgs/src/atheros/src/atl1e_main.c:313: error: ‘struct net_device’ has no member named ‘vlan_rx_register’
/home/mgalgs/src/atheros/src/atl1e_main.c:316: error: ‘struct net_device’ has no member named ‘poll_controller’
make[2]: *** [/home/mgalgs/src/atheros/src/atl1e_main.o] Error 1
make[1]: *** [_module_/home/mgalgs/src/atheros/src] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.31-14-generic'
make: *** [default] Error 2
```

I've got the same lspci output and everything. I'm using an ACER Aspire 5739G.

---

### Post by mitch_feaster on 2009-10-29
> **mitch_feaster said:**
> Has anyone tried this in 9.10? When I try to compile the driver I get the following errors:



After setting acpi=off in grub2 everything just worked (i.e. I didn't need to compile drivers)... It "fixed" the wifi too...

---

### Post by baronrouge on 2010-02-28
Latest version of the driver from [http://partner.atheros.com/Drivers.aspx ]("http://partner.atheros.com/Drivers.aspx")worked great for me on 9.10 with the above instructions. Not sure what went wrong as it had been working fine for days since install, seems fixed now anyway.

EDIT: Actually it didn't. After couple of restarts I'm back to square 1. I'll try acpi=off in GRUB and report

---

### Post by tehowe on 2010-05-20
Okay, so

> tar -zxf AR81Family-linux-v1.0.1.9.tar.gz
cd src/
make
sudo make install
I've tried this and simply received a 'Linux Kernel Source Not Found. Stop." error on either of the make commands specified in this thread. This is on Ubuntu Studio Lynx.

I found this manpage about installing a driver called alc for the Atheros network card, will see how that goes...

[http://manpages.ubuntu.com/manpages/lucid/man4/alc.4freebsd.html#toptoc7](http://manpages.ubuntu.com/manpages/lucid/man4/alc.4freebsd.html#toptoc7)

It calls for putting two lines in your kernel configuration file.

> **device** **miibus**
**device** **alc**
Update: Where's the kernel config file?

---

### Post by mitch_feaster on 2010-05-20
This issue hasn't existed for me since about kernel 2.30 ish, but I guess if you're trying to compile the drivers it's because it's not working for you... What laptop/ethernet chipset is it?

---

### Post by tehowe on 2010-05-20
> **mitch_feaster said:**
> This issue hasn't existed for me since about kernel 2.30 ish, but I guess if you're trying to compile the drivers it's because it's not working for you... What laptop/ethernet chipset is it?

Hi Mitch these are the two devices that weren't detected;

> >lspci
01:00.0 Ethernet controller: Atheros Communications AR8131 Gigabit   Ethernet (rev c0)
02:00.0 Network controller: Intel Corporation WiFi Link 1000 SeriesThe laptop is the Acer1410 ('olympic') netbook as well.

I don't know if the following will help, but people usually ask for this info...

> > sudo lshw -C network
*-network DISABLED      
       description: Ethernet interface
       product: AR8131 Gigabit Ethernet
       vendor: Atheros Communications
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: eth0
       version: c0
       serial: 00:26 x x x x
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vpd bus_master cap_list ethernet   physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=atl1c   driverversion=1.0.0.1-NAPI firmware=N/A latency=0 link=yes multicast=yes   port=twisted pair
       resources: irq:16 memory:93500000-9353ffff ioport:2000(size=128 )
  *-network DISABLED
       description: Wireless interface
       product: WiFi Link 1000 Series
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlan0
       version: 00
       serial: 00:1e x x x x
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet   physical wireless
       configuration: broadcast=yes driver=iwlagn latency=0   multicast=yes wireless=IEEE 802.11bgn
       resources: irq:28 memory:92500000-92501fffThanks for any help you can provide. This notebook's like a year old and the network card worked fine under Wubi so it *should* work, but doesn't.

Update: I tried the 'acpi=off' suggestion in grub, no change.

---

### Post by mitch_feaster on 2010-05-20
Interesting... I have the exact same ethernet controller and it's all working for me in Lynx without driver-compiling fun... I can't comment on the wifi chipset...

---

### Post by tehowe on 2010-05-20
> **mitch_feaster said:**
> Interesting... I have the exact same ethernet controller and it's all working for me in Lynx without driver-compiling fun... I can't comment on the wifi chipset...

Do you think it might have something to do with Studio and their special *2.6.32-21-preempt x86_64* kernel?

But that should be the same as the standard fork kernel except for the audio interrupts, right? (I don't really understand the architecture yet, so I'm working off of instinct.) =/

Too bad really, this is like the perfect little Ubuntu netbook. Hopefully it can get sorted out.

---

### Post by mitch_feaster on 2010-05-20
> **tehowe said:**
> Do you think it might have something to do with Studio and their special *2.6.32-21-preempt x86_64* kernel?

But that should be the same as the standard fork kernel except for the audio interrupts, right?

Oh man, that sounds like fun! I'm afraid I honestly have no idea, but my instincts agree with yours. It would be interesting to see what kernel configuration messed with the ethernet driver...

---

### Post by tehowe on 2010-05-20
> **mitch_feaster said:**
> Oh man, that sounds like fun! I'm afraid I honestly have no idea, but my instincts agree with yours. It would be interesting to see what kernel configuration messed with the ethernet driver...

I found something on this old thread about an HP card notebook problem that helped...

[http://ubuntuforums.org/showpost.php?p=9318319&postcount=12](http://ubuntuforums.org/showpost.php?p=9318319&postcount=12)

You plug in your ethernet and type 

> sudo dhclient eth0

Then you 

> 
sudo apt-get update
sudo apt-get install wicd

The mysterious incantations worked. :) Wicd doesn't look like the standard Lynx network manager, it seems to be some older Python app but it works and I'm on wired eth0. It detects wireless networks too, though my corporate network is password protected and I haven't gotten on there yet. Looking good though.

---

