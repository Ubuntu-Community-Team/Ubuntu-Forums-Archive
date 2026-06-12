---
title: "Network card is not detected"
date: 2010-02-14
forum: Hardware
---

### Post by krishnan_sriram on 2010-02-14
I have a new Gateway laptop - NV 59. I have setup a dual boot on my laptop - Windows 7 and Ubuntu 9.04.

All is fine in Ubuntu, except for internet connectivity.
1. Ubuntu does not detect my "Wired network connection". I looked to see if my "eth0" is even being detected from Network Manager and "ifconfig -a" optiion.Unfortunately not. 

2. I am not sure what to do next. But there are no issues on identifying wireless connectivity. All seem to fine. As I have wirec connection at home, I am sesiously disabled.

Note: I back tracked. I tried ubuntu 8.10 too. Same issues there too. So I guess, historially there was less support for Gateway laptops. Can some one help????

Regards,
Krishnan

---

### Post by drpjkurian on 2010-02-14
Hi
It seems that you are not having appripriate drivers for your card. Please type the command ```
lspci
``` in terminal and find out the make of your card. Google it for drivers and install it.

---

### Post by krishnan_sriram on 2010-02-20
Ok. Here are the steps to be followed to overcome this issue
1. Check to see if wired ethernet card is detected
2. Install ethernet driver
3. Enjoy surfing

How to know if wired ethernet card is detected
$> ifconfig 

This commmand should show you something like this
eth0      Link encap:Ethernet  HWaddr 00:26:2d:77:87:05  
          inet addr:192.168.0.3  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::226:2dff:fe77:8705/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:19035 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12891 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:25890433 (25.8 MB)  TX bytes:1420812 (1.4 MB)
          Interrupt:16 

if not proceed to step 2

Install Ethernet driver
You need to identify your wired network card manufacturer
You can do this by different ways

[LIST=1]
[*]$> lspci
[LIST=1]
[*]look for the line like the containing "Ethernet controller"
[*]In my case it was
[*]02:00.0 Ethernet controller: Broadcom Corporation Device 1692 (rev 01)
[/LIST]
[*]Once we know the manufacturer, you have to find out the driver that 'sto be downloaded and installed in your box.
[*]In my case it was [www.broadway.com](www.broadway.com) and I went into their drivers download page - [http://www.broadcom.com/support/ethernet_nic/downloaddrivers.php](http://www.broadcom.com/support/ethernet_nic/downloaddrivers.php)
[*]Tough part is identifying the chipset and corresponding driver for download.
[LIST=1]
[*]I tried lshw, but it threw massive output and I was not able to figure out any useful information from it (my poor knowlkedge in LINUX may have contributed to this)
[*]I logged into windows and followed in the instructions mentined in this page - [http://www.broadcom.com/support/ethernet_nic/determine_driver.php](http://www.broadcom.com/support/ethernet_nic/determine_driver.php)
[/LIST]
[*]Downloaded appropriate driver. In my case it was  "tg3-3.99k--1"
[*]Created seperate directory "tg3", and copied my driver file
[LIST=1]
[*]tar xvzf tg3-<version>.tar.gz
[*]Go into the inner-most directory. In my casse it was "/Downloads/Linux/Driver/tg3/tg3-3.99k"
[*]execute the command 'make'
[*]This will create one of the 2 files -  insmod tg3.o or insmod tg3.ko
[*]Execurte the command 'make install'
[/LIST]
[*]Once all of the steps execute successfully, try this command 'ethtool eth0
[LIST=1]
[*]This should show you appropriate information about the network card
[/LIST]
[*]Enjoy surfing
[/LIST]
  
Regards,
Krishnan

---

