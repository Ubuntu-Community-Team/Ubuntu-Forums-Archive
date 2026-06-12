---
title: "Broadcom BMC4313 drivers, Ubuntu 11.04."
date: 2011-07-17
forum: Hardware
---

### Post by trustinglittle on 2011-07-17
Hello all,

This is my first post to any forum, so if I'm doing it wrong let me know! :-)

I've tried everything I can think of plus Google with no results. So I'll lay out the details:

---Lenovo B570 notebook/laptop (whatever suits your fancy)

--Ubuntu 11.04

--Broadcom BMC4313 wireless card

---System>Administration>Additional Drivers -> Green Light for Broadcom STA wireless driver (activated and currently in use)

---The networking Icon has the following grayed out options: Wired Network, Wireless Networks, wireless is disabled by hardware switch, & Enable wireless.  I don't know why Wired Network is grayed out because it's working now.  I get the wireless networks grayed out but Enable Wireless and disabled by hardware switch beats me.

---I Checked the bios and turned off then back on the wireless card, reinstalled the drivers.

---On the front of the computer there is a switch for the card that worked in windows, I switched that on and off.

---I commented out all the lines in /etc/modprobe.d/blacklist-bcm43.conf

All the above didn't work.  :-/  So I'm in suspense to see if this can be resolved :-D

It should be noted that a few days ago I was running windows (can't stand it) because the wireless driver worked, put the computer to sleep and when I brought it back up it's as if windows was having a smiler problem.  The wireless card was recognized and running but disabled (?).  The card never worked with Ubuntu.

I hope that's plenty of info to get the help started.  MANY THANKS in advance!

---

### Post by Cybie257 on 2011-07-17
If I am correct, you are having these issues across platforms (Windows and Linux). It sounds like a possible issue that could need a BIOS update. I would check the site for your computer and BIOS updates to see if there is one that relates to wireless problems. 

-Cybie

---

### Post by trustinglittle on 2011-07-17
I'm not to sure, new comp, and I it did work in win7. But I'll give it a shot anyway and let you know!  Thanks!

---

### Post by trustinglittle on 2011-07-17
I checked out the BIOS.  They're up to date.

---

### Post by trustinglittle on 2011-07-18
Ok I think it has to do with the wireless on off switch.  I'm going to give this thread a shot...

---http://ubuntuforums.org/showthread.php?t=1753072&highlight=Wireless+disabled+hardware+switch

---

### Post by trustinglittle on 2011-07-18
bump

I tried some ideas from this link

---http://ubuntuforums.org/showthread.php?t=1755670

It explains a procedure for HP's in terms of 3 different states of the wireless card.  the Hardware switch really controls software.  No mater what combination I use of Disabled, Enabled and off, Enabled and On with the switch on or off while shutting down windows and starting up Ubuntu.

rfkill list shows that the the wireless adapter is blocked via software but not hardware.

Still need some help.  Thanks!

---

### Post by trustinglittle on 2011-07-19
bump

Anybody?  Need a hand with this one.

---

### Post by rmrlambert on 2011-07-23
Hi Trustinglittle,

I have a Compaq 6310 with a Broadcom 4311 wifi and I've been having the same problem as you.  I tried everything and this is the only thing that worked.  So try this:

sudo apt-get install b43-fwcutter
sudo apt-get install firmware-b43-installer

Wifi started working without any further action.  I am running Ubuntu Studio and all of the wireless networks started appearing under the networking icon next to the clock.

Best of luck with this..
RMRLambert

---

### Post by the_executioner on 2011-07-23
yea i had the same prob ........... solved it today 
i am pretty sure we wouldve had the same prob 
but anyway gimme more specs as in ure post the result of these following commands
lspci 
lshw -c network 
iwconfig 
and tell me if the wireless worked right after the install of natty or at any other time that it worked

---

### Post by trustinglittle on 2011-07-25
Thank's for you help.  However, even after I turn the wireless from disabled to enabled, it says wireless disabled under wireless networks.
-TL

---

### Post by trustinglittle on 2011-07-25
lspci

> 00:00.0 Host bridge: Intel Corporation 2nd Generation Core Processor Family DRAM Controller (rev 09)
00:02.0 VGA compatible controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09)
00:16.0 Communication controller: Intel Corporation 6 Series Chipset Family MEI Controller #1 (rev 04)
00:1a.0 USB Controller: Intel Corporation 6 Series Chipset Family USB Enhanced Host Controller #2 (rev 05)
00:1b.0 Audio device: Intel Corporation 6 Series Chipset Family High Definition Audio Controller (rev 05)
00:1c.0 PCI bridge: Intel Corporation 6 Series Chipset Family PCI Express Root Port 1 (rev b5)
00:1c.1 PCI bridge: Intel Corporation 6 Series Chipset Family PCI Express Root Port 2 (rev b5)
00:1c.3 PCI bridge: Intel Corporation 6 Series Chipset Family PCI Express Root Port 4 (rev b5)
00:1d.0 USB Controller: Intel Corporation 6 Series Chipset Family USB Enhanced Host Controller #1 (rev 05)
00:1f.0 ISA bridge: Intel Corporation HM65 Express Chipset Family LPC Controller (rev 05)
00:1f.2 SATA controller: Intel Corporation 6 Series Chipset Family 6 port SATA AHCI Controller (rev 05)
00:1f.3 SMBus: Intel Corporation 6 Series Chipset Family SMBus Controller (rev 05)
02:00.0 Network controller: Broadcom Corporation BCM4313 802.11b/g/n Wireless LAN Controller (rev 01)
03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 06)

lshw -c network
>   *-network DISABLED      
       description: Wireless interface
       product: BCM4313 802.11b/g/n Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth1
       version: 01
       serial: c0:f8:da:41:3c:bd
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl0 driverversion=5.100.82.38 latency=0 multicast=yes wireless=IEEE 802.11
       resources: irq:17 memory:d0500000-d0503fff
  *-network
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 06
       serial: f0:de:f1:5d:1c:bd
       size: 100Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full ip=192.168.1.9 latency=0 link=yes multicast=yes port=MII speed=100Mbit/s
       resources: irq:40 ioport:2000(size=256) memory:d0404000-d0404fff memory:d0400000-d0403fff


iwconfig
> 
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11  Access Point: Not-Associated   
          Link Quality:5  Signal level:0  Noise level:0
          Rx invalid nwid:0  invalid crypt:0  invalid misc:0


---The wireless never worked with Linux.  I do think the drivers work it's just the hardware switch problem.

Sorry it took so long to respond.

---

### Post by trustinglittle on 2011-07-25
bump

Thanks for the help so far!

---

### Post by trustinglittle on 2011-07-26
BUMP

Still cracking away...

---

### Post by trustinglittle on 2011-07-27
Bump

---

### Post by trustinglittle on 2011-07-29
Bump

---

### Post by trustinglittle on 2011-08-08
SOLVED

Ok, so network-manager doesn't play nice with my hardware.

-Uninstall network-manager and install wicd (pronounced wicked)
-Reboot
-Applications > Internet > WICD Network Manager

> sudo apt-get install wicd && sudo apt-get remove network-manager*

Got to give credit where credit is do so...
Thanks to:

[http://fakkelbrigade.eu/chris/blog/2010/12/wireless-not-working-in-ubuntu-on-the-lenovo-ideapad-s12/](http://fakkelbrigade.eu/chris/blog/2010/12/wireless-not-working-in-ubuntu-on-the-lenovo-ideapad-s12/)

SOLVED

---

### Post by trustinglittle on 2011-08-08
Bump

---

