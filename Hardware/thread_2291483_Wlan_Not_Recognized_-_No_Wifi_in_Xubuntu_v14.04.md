---
title: "Wlan Not Recognized - No Wifi in Xubuntu v14.04"
date: 2015-08-20
forum: Hardware
---

### Post by Rick St. George on 2015-08-20
Have installed Xubuntu v14.04 on HP/Compaq Presario F500 (64bit). There is a switch in front, that when on turns WiFi light from Orange to Blue. Will not turn to Blue upon Boot-up. Worked fine in Windows (now gone). Ran the following commands to detect status, etc.

```

regina@regina-HPF500-ABA:~$ lspci
Network Controller: Broadcom Corp. BCM4311 802.11b/g Wlan (rev 01)


regina@regina-HPF500-ABA:~$ iw dev wlan0 link
command failed: No such device (-19)


regina@regina-HPF500-ABA:~$ ethtool eth0
Settings for eth0:
    Supported ports: [ MII ]
    Supported link modes:   10baseT/Half 10baseT/Full 
                            100baseT/Half 100baseT/Full 
    Supported pause frame use: No
    Supports auto-negotiation: Yes
    Advertised link modes:  10baseT/Half 10baseT/Full 
                            100baseT/Half 100baseT/Full 
    Advertised pause frame use: No
    Advertised auto-negotiation: Yes
    Speed: 100Mb/s
    Duplex: Full
    Port: MII
    PHYAD: 1
    Transceiver: external
    Auto-negotiation: on
Cannot get wake-on-lan settings: Operation not permitted
    Link detected: yes


regina@regina-HPF500-ABA:~$ ip link show
1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN mode DEFAULT group default 
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
2: eth0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc pfifo_fast state UP mode DEFAULT group default qlen 1000
    link/ether 00:1b:24:47:a6:f8 brd ff:ff:ff:ff:ff:ff


regina@regina-HPF500-ABA:~$ ethtool wlan0
Settings for wlan0:
Cannot get device settings: No such device
Cannot get wake-on-lan settings: No such device
Cannot get message level: No such device
Cannot get link status: No such device
No data available


```

Trying to work through suggestions at this post;
[http://ubuntuforums.org/showthread.php?t=2214110](http://ubuntuforums.org/showthread.php?t=2214110)
But get "unable to locate package firmware-b43-installer".
Any suggestions for getting Wlan and WiFi to work?
Thanks
):P

---

### Post by Rick St. George on 2015-08-20
Please Note: it may also be related to another Thread I posted (with no answer yet) on this same laptop.
[http://ubuntuforums.org/showthread.php?t=2288124](http://ubuntuforums.org/showthread.php?t=2288124)

---

### Post by Rick St. George on 2015-08-20
I had RUN THESE COMMANDS
```

sudo apt-get remove --purge bcmwl-kernel-source

sudo rm /etc/modprobe.d/blacklist-bcm43.conf

sudo rm /etc/modprobe.d/broadcom-sta-common.conf

sudo apt-get install b43-fwcutter firmware-b43-installer

sudo reboot

```

But still got "unable to locate package firmware-b43-installer".

------------------

Problem solved: I used the instructions under B43-No Internet Access driver at below link.
Note: this also solved a previous problem of shutdown - see referenced Link above.

Followed instructions at this Link;
[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx#b43%20-%20Internet%20access](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx#b43%20-%20Internet%20access)

Found Many threads that were older and NOT VALID. The page above will take you step by step installing the drivers for the various Broadcom WiFi devices, onto the Ubuntu flavors upto and including v14.04.

Case Closed.

---

