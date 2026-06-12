---
title: "Ubuntu experience with Dell D610"
date: 2005-07-11
forum: Hardware &amp; Laptops
---

### Post by Phill_G on 2005-07-11
Hi, I just purchased a Dell D610 and I plan to install Ubuntu when it arrives.  I am wondering if anyone has tried an install on the D610 and, if so, what problems may have come up.  In particular I am concerned with these areas:

1) Pentium M power management (clock speed modulation?)

2) WLAN support / modem support

3) Graphics support

4) Memory (full usage).

The unit has the following options related to the items above:

1) Centrino/Pentium M 750 1.86 GHz

2) Intel PRO Wireless 2200 b/g miniPCI / standard modem

3) SXGA+ screen / ATI RADEON X300 

4) 1GB 533 MHz bus ram.

I use unix/linux quite often and I've installed a distribution or two on some older computers but I generally don't dig too deep into the configuration and I've never had to deal with hardware issues.  I most probably will not be able to get these items to work if it so happens they don't.  I've looked online for some info on the D610 and I ran across these issues with several other Linux distributions, so I am trying to see if such problems exist with Ubuntu.  Anyone know of some nice websites that would have an install guide?  I already checked tuxmobile and I see an Ubuntu install only for the D600.

Thanks,

-Phill

---

### Post by emperor on 2005-07-11
It is possible to get all that you listed working properly. You can use the i6000 and i9300 entries at [http://www.linux-laptop.net/]("http://www.linux-laptop.net/"). Look at both the Ubuntu and Debian reports. There is also some usefull entries in other distro reports on the common issues like the xorg modifications and ati fglrx driver.

The biggest problem for me was getting DMA working on the DVD/cdrom drive. See the thread on the i9300 for further details and resolution. You will need to modifiy and compile a kernel to resolve this issue.

You will need to install the firmware to get the wireless working and edit a config file to get the centrino to shift from 1/2 to full speed.

You will have the greatest success with Ubuntu and the excellant support and documentation that is available.

---

### Post by bugmenot on 2005-08-20
Here's a site that has good details on getting everything working: [http://home.comcast.net/~canez/d610/](http://home.comcast.net/~canez/d610/)

Hope this helps!

---

### Post by Luna.jp on 2007-11-03
Hello all.

I am a Dell D610 user and I have installed Ubuntu Feisty Fawn on here. Everything works great except the wireless. I have searched for about two days and after installing, breaking, reinstalling and updating, I have yet to come across a clear cut answer to my problem of getting wireless to work.

This laptop uses the Intel PRO/wireless 2915 A/B/G which I believe can be cross applied to Intel Pro/Wireless 2200BG.

According to this page of Hardware Support ( [https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsIntel](https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsIntel) ) the wireless card does work and is "Automatically detected" and works right out of the box.

I still haven't gotten my wireless light to come on nor do I see it being recognized by the system.
Can anyone else who uses a D610 offer some help in this area?

---

### Post by Luna.jp on 2007-11-06
This is what I got when starting up my network...

```


luna@Dellnix:~$ sudo /etc/init.d/networking start
 * Configuring network interfaces...                                            There is already a pid file /var/run/dhclient.eth0.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/eth0/00:14:22:d6:04:e3
Sending on   LPF/eth0/00:14:22:d6:04:e3
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 5
DHCPOFFER from 192.168.1.1
DHCPREQUEST on eth0 to 255.255.255.255 port 67
DHCPACK from 192.168.1.1
bound to 192.168.1.102 -- renewal in 36931 seconds.
eth1: ERROR while getting interface flags: No such device
There is already a pid file /var/run/dhclient.eth1.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

SIOCSIFADDR: No such device
eth1: ERROR while getting interface flags: No such device
eth1: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up eth1.
eth2: ERROR while getting interface flags: No such device
There is already a pid file /var/run/dhclient.eth2.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

SIOCSIFADDR: No such device
eth2: ERROR while getting interface flags: No such device
eth2: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up eth2.
ath0: ERROR while getting interface flags: No such device
There is already a pid file /var/run/dhclient.ath0.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

SIOCSIFADDR: No such device
ath0: ERROR while getting interface flags: No such device
ath0: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up ath0.
wlan0: ERROR while getting interface flags: No such device
There is already a pid file /var/run/dhclient.wlan0.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

SIOCSIFADDR: No such device
wlan0: ERROR while getting interface flags: No such device
wlan0: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up wlan0.
                                                                         [ OK ]
luna@Dellnix:~$ 



```

The light still doesn't come on and still no wireless =(

Any help?

---

