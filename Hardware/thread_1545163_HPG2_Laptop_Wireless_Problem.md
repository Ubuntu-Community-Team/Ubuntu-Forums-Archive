---
title: "HPG2 Laptop Wireless Problem"
date: 2010-08-03
forum: Hardware
---

### Post by ezm on 2010-08-03
Hi:

I just got a new HPG62 and am tryng to install Ubuntu 10.04.  I am having trouble with the wireless.  Initially, I had installed the OS and run the update manager and the wireless was working fine.  Then I tried to install VMware Player and installed a Virtual Machine; at that stage the wireless stopped working.  I tried to reinstall Ubuntu from scratch (presumably erasing the previous installation) and I am still having the same problem.  Basically, in the network manager I can connect to a wired network easily, but the manger does not list _any_ wireless networks at all.

I think the card is running a driver and it seems to be configured properly.  When I run lshw -C network, I get the following:

[INDENT] *-network               
       description: Wireless interface
       product: Realtek Semiconductor Co., Ltd.
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlan0
       version: 10
       serial: 70:f1:a1:ed:be:96
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rtl819xSE driverversion=0015.0127.2010 firmware=62 latency=0 multicast=yes wireless=802.11bgn
       resources: irq:16 ioport:3000(size=256) memory:d3000000-d3003fff
[/INDENT]
From this it seems to me that the driver is installed.  iwconfig also shows infor for wlan0: 

[INDENT]wlan0     802.11bgn  Nickname:"rtl8191SEVA2"
          Mode:Managed  Frequency=2.417 GHz  Access Point: Not-Associated   
          Bit Rate:135 Mb/s   
          Retry:on   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality=10/100  Signal level=0 dBm  Noise level=-100 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
[/INDENT]

So I am a bit at a loss here.  Could the device somehow be turned off?  Could the VMware Player somehow have altered the configuration or turned the device off?  Any help would be much appreciated.

---

### Post by kernelles on 2011-01-01
I"m looking at buying this same laptop and putting 10.10 on it. I see you have no replies, but did you ever solve this problem?

---

