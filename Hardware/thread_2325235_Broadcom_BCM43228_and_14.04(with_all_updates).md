---
title: "Broadcom BCM43228 and 14.04(with all updates)"
date: 2016-05-20
forum: Hardware
---

### Post by lsutiger on 2016-05-20
This is not a new install. I have been running 14.04 since October 2014. I am attempting to upgrade my wifi card to a dual band card. I got my hands on the one mentioned in the title. 
I know Broadcom and Linux do not play well together, but I have been able to get Broadcom cards to work in the past (and this one was free)
I have been attempting different solutions over the last two days to get the Broadcom BCM43228 wireless chip to work. The last round this morning, I documented each step and will post in this thread the steps and the results. I have had some progress but still no wireless connection. Also, I am working remotely at the moment via ssh.
Here we go!
My hardware:
```
sudo lspci | grep -i Network
02:00.0 Network controller: Broadcom Corporation BCM43228 802.11a/b/g/n

```
The driver:
```
lspci -vv -s 02:00.0 | grep driver
Kernel driver in use: wl
```
More info
```
sudo lshw -C network
  *-network DISABLED
       description: Wireless interface
       product: BCM43228 802.11a/b/g/n
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlan2
       version: 00
       serial: 24:fd:52:fe:4b:5f
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl0 driverversion=6.30.223.248 (r487574) latency=0 multicast=yes wireless=IEEE 802.11abg
       resources: irq:18 memory:f0100000-f0103fff

rfkill list all
3: brcmwl-0: Wireless LAN
	Soft blocked: yes
	Hard blocked: yes

Unblocked with 
rfkill unblock all
restart

1: brcmwl-0: Wireless LAN
	Soft blocked: no
	Hard blocked: yes
```
Steps taken:
```
sudo apt-get update
sudo apt-get upgrade
sudo apt-get install linux-headers-generic
sudo apt-get install --reinstall bcmwl-kernel-source
```
No wifi
Do I have a wireless interface?
```
iwconfig
wlan2     IEEE 802.11abg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off

```
Try to bring it up:```

sudo ifconfig wlan2 up
sudo lshw -C network
  *-network
       description: Wireless interface
       product: BCM43228 802.11a/b/g/n
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlan2

```
Progress!
Scan wireless:
```
sudo iwlist wlan2 scan
wlan2     Interface doesn't support scanning : Invalid argument
```
??
And it is still hard blocked:
```
1: brcmwl-0: Wireless LAN
	Soft blocked: no
	Hard blocked: yes
```

I do not have any type of hardware switch on the computer for wifi(or anything else). There is a keyboard shortcut that will turn on Soft block.
In the end, if I can not get this card working, could someone suggest a dual band wifi card that works oob? The model of computer is an Acer AS5560-7414.

Thanks!

---

### Post by ajgreeny on 2016-05-20
See if this thread is any use for you:-
[http://ubuntuforums.org/showthread.php?t=2214110](http://ubuntuforums.org/showthread.php?t=2214110)

I generally do not use wifi but a cable connection, and the machines that do use wifi are all atheros cards or Intel, all of which seem to work out of the box, so I have no personal experience of getting BCM cards to work, so here's hoping this helps you.

---

### Post by lsutiger on 2016-05-20
Thanks!
I'll start researching Atheros cards

---

