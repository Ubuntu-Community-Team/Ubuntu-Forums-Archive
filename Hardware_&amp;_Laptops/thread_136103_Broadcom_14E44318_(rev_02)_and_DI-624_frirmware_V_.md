---
title: "Broadcom 14E4:4318 (rev 02) and DI-624 frirmware V 2.50 and linux"
date: 2006-02-25
forum: Hardware &amp; Laptops
---

### Post by olidel on 2006-02-25
Hello,

       Is someone, somewhere in the world successfully run with success the following setup ? I have a laptop which is a compaq presario V2555US equiped with a Broadcom 14E4:4318 (this is the result of a lspci -n) and a DI-624 from dlink with firmware version 2.50. I tried to use breezy and that didn't work with ndiswrapper. So, I tried to use Dapper flight 4 and it doesn't work either. Althought, everything seems to be ok because the wireless network is detected, I can see that with the iwconfig command and also with the ifconfig command. In spite of that I cannot reach my home network through the wireless card. I tried that with encryption without encryption with static IP address and with DHCP but nothing works. Btw have a dual boot on this machine and everything is running fine with windows xp.  To give you an idea this is the result when I try to run the "sudo dhclient eth1" with dapper  :

[B]
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

Listening on LPF/eth1/00:14:a5:2f:f6:fc
Sending on   LPF/eth1/00:14:a5:2f:f6:fc
Sending on   Socket/fallback
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 21
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 5
No DHCPOFFERS received.
No working leases in persistent database - sleeping.[/B]


I must tell you that I have some difficulties to get the MAC address of the access point but even when I am succesfull I have the above error. For my wireless card I used the firmware found in the bcmwl5.sys file which is on the xp partition.

Thanks for your help.

Olivier.

---

### Post by esmclega on 2006-02-26
I am also having the same problem with the same router and broadcom wireless. If anybody has any ideas I would greatly appreciate it. Thanks.

---

### Post by olidel on 2006-02-26
Hello,

    Finally, I made it works  !!!!! _BUT_ not thepti way I expected. In fact, it is working but not with the parameter that I wanted to use in the first step e.g. I cannot use WEP encryption of 128 bits, I cannot either use the Shared key parameter. Instead of this I managed to use 64 bits WEP encryption with open parameter. So this is what I have done :

*on the router DI-624 :

- Install the latest firmware from dlink U.S.A. version 2.70.
- Configure the DI-624 with 802.11g only
- Configure the DI-624 with 64 bits WEP key and with open parameter.

* on the laptop :

- install all the wireless stuff as indicated in the different newsgroup or forum
- Removed the bcm43xx module (if it is loaded)
- reloaded the bcm43xx module
- Ran the following command : iwconfig eth1 essid "my_essid" key open my_key
- Ran this command : sudo iwconfig eth1 ap my_router_mac_address
- Ran the dhclient eth1 command.

I also built  the following script in the /etc/init.d directory and with the appropriate symbolic link so the interface would start at the boot of the laptop


[B]#!/bin/sh
#

PATH=/sbin:$PATH
WLAN_INTERFACE=eth1
MAC_ADDRESS=00:0d:88:b7:a0:c4
MODULE=bcm43xx

case "$1" in
start)
    echo "Start of " $WLAN_INTERFACE
    iwconfig $WLAN_INTERFACE ap $MAC_ADDRESS
    dhclient $WLAN_INTERFACE
    ;;
restart)
    echo "Restart of " $WLAN_INTERFACE
    modprobe -r bcm43xx
    modprobe bcm43xx
    iwconfig $WLAN_INTERFACE ap $MAC_ADDRESS
    modprobe bcm43xx
    iwconfig $WLAN_INTERFACE ap $MAC_ADDRESS
    dhclient $WLAN_INTERFACE
    ;;
stop|reload|force-reload)
    ;;
esac

exit 0[/B]

A few notes :

- It works with the ndiswrapper module or the bcm43xx module. The ndiswrapper module is ok as long as you don't press the on/off wireless switch. If you do that you must redo the steps on the laptop that I have showed above.
- I didn't test other encryption method supported by the card and the router such as WPA.

   So, in conclusion there is something definitely wrong with the linux driver and with this hardware setup, but this is a workaround with all the drawback that I have showed. Btw, I'm writing on this forum through my wireless connection ;-).

Hope this will help.

Olivier.

---

### Post by olidel on 2006-02-26
Hello,

     Just a word to tell you that it is also working without encryption at all.

Thanks.

Olivier

---

### Post by esmclega on 2006-02-26
I will give it a try. Thank you.

---

### Post by olidel on 2006-03-03
Hello,

     I have made new tests. So, I can tell you that with the above hardware setup, i can run a secure wireless connection in WPA-PSK mode with cipher AES between my laptop and my DI-324. This is working only with the ndiswrapper module because the wpa_supplicant daemon support ndiswrapper but not the bcm43xx driver. I tried to use the WPA2 secure connection but without success. I also noticed that if the essid is not broadcast it doesn't work, although it should work.
      So, in conclusion I have now a wireless network which is much more robust than before because I'm using WPA which is much better than the wep protocol. There is however a solution which go one step further and which is also a standard from the IEEE organisation and this is WPA2 also known as 802.11i. This is where  I should be but unfortunately it doesn't work yet in my environment.


Hope this help.

Thanks.

Olivier

---

### Post by kenjiru on 2007-06-16
Any update on this topic?

---

