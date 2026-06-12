---
title: "Issues with Intel Wireless Card"
date: 2011-08-25
forum: Hardware
---

### Post by more cowbells on 2011-08-25
Hi everyone, I just recently set my Dell XPS 15 laptop up to dualboot Ubuntu 11.04 and Windows.  Everything was fine with the installation but for some reason Ubuntu will not let me access wifi.  I have an Intel Centrino Wireless-N 1030 and it shows up when I run lspci but the wireless button in the internet connection dropdown shows "wireless networks" grayed out.

The weird thing though was that in the Ubuntu live cd environment before I installed, the wifi was working and showed a list of all available networks around me.  Any help would be appreciated.

Thanks! :)

---

### Post by fdrake on 2011-08-25
can you post the results of this commands:
```
iwconfig
lspci -vvv | grep eless
sudo lshw  -c network

```

---

### Post by more cowbells on 2011-08-25
Thanks for the reply :)  here are the outputs of the commands you listed:

iwconfig:
```

lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=off   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on


```lspci -vvv | grep eless:
```

03:00.0 Network controller: Intel Corporation Centrino Wireless-N 1030 (rev 34)
    Subsystem: Intel Corporation Centrino Wireless-N 1030 BGN


```
sudo lshw -c network:
```

  *-network DISABLED      
       description: Wireless interface
       product: Centrino Wireless-N 1030
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wlan0
       version: 34
       serial: bc:77:37:09:84:31
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwlagn driverversion=2.6.38-11-generic firmware=17.168.5.2 build 35905 latency=0 link=no multicast=yes wireless=IEEE 802.11bgn
       resources: irq:50 memory:f1b00000-f1b01fff
  *-network
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:06:00.0
       logical name: eth0
       version: 06
       serial: 14:fe:b5:9a:49:c5
       size: 1Gbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full ip=10.17.100.19 latency=0 link=yes multicast=yes port=MII speed=1Gbit/s
       resources: irq:43 ioport:2000(size=256) memory:f1804000-f1804fff memory:f1800000-f1803fff


```

---

### Post by fdrake on 2011-08-25
> **more cowbells said:**
> 
```

  *-network [COLOR="Red"]**_DISABLED_**[/COLOR]      
       description: Wireless interface
       product: Centrino Wireless-N 1030
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wlan0
       version: 34
       serial: bc:77:37:09:84:31
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwlagn driverversion=2.6.38-11-generic firmware=17.168.5.2 build 35905 latency=0 link=no multicast=yes wireless=IEEE 802.11bgn
       resources: irq:50 memory:f1b00000-f1b01fff
  

```


can you post the results of:
```
less /var/lib/NetworkManager/NetworkManager.state
```


do you by the chances have an external switcher on the side of the laptop?
[IMG]http://www.dell.net76.net/images/dell-xps-15z-battery/dell-xps-15z-battery-rthumb-441.jpg[/IMG]

---

### Post by more cowbells on 2011-08-25
Here you go:

```
[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
/var/lib/NetworkManager/NetworkManager.state (END) 

```And I'm not sure if I know what you mean by an external switcher.

EDIT:  just saw the picture you put in, and no my laptop doesn't have that.  What exactly does it do?  XPS 15 does have a function key for enabling and disabling wifi but I tried that as well with no success.

---

### Post by fdrake on 2011-08-25
do you have a way to know if the switch is on the OFF or ON side?
(some kind of led that turns one? or a written marks on / off?)
also while playing with that do:

```

sudo service network-manager stop
sudo rm /var/lib/NetworkManager/NetworkManager.state
sudo service network-manager start

```
to restart the netmngr

edit. you have to press those functions keys to turn it on. ubuntu won't be able to do it by itself if the key is off!

---

### Post by more cowbells on 2011-08-25
It works now!

It was set to on before but I pressed it a couple of times and now it is working.
Not sure why it wasn't working before though 

Thank you so much for your help! :)

---

### Post by fdrake on 2011-08-25
> **more cowbells said:**
> It works now!

It was set to on before but I pressed it a couple of times and now it is working.
Not sure why it wasn't working before though 

Thank you so much for your help! :)

i m :D 4 u
:guitar:

ps make sure to mark this thread as solved so other ppl with ur same issue can look at it.

---

