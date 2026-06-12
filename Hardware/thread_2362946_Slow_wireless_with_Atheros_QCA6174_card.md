---
title: "Slow wireless with Atheros QCA6174 card"
date: 2017-06-04
forum: Hardware
---

### Post by mikewiz38 on 2017-06-04
I have a Dell XPS 13 9360 laptop running Ubuntu 17.10.  I have the following wireless card in my system...

Qualcomm Atheros QCA6174 802.11ac Wireless Network Adapter (rev 32)

If I boot up into Windows and run an iperf test to my pfsense box, I get about 102Mbits/sec.  If I boot up into Ubuntu, I get 10Mbit/sec.  Now the odd thing is that if I go over to a comcast speedtest page in Ubuntu, I get 150Mbps.  

I was wondering if anybody had any ideas of why this is happening and how to get a decent speed under Ubuntu.

Thanks!

---

### Post by jeremy31 on 2017-06-04
Try disabling power management for the wifi
```
sudo sed -i 's/wifi.powersave = 3/wifi.powersave = 2/' /etc/NetworkManager/conf.d/default-wifi-powersave-on.conf
```
```
systemctl restart network-manager.service
```

Post results for ```
cat /etc/lsb-release
```

---

### Post by mikewiz38 on 2017-06-09
> **jeremy31 said:**
> Try disabling power management for the wifi
```
sudo sed -i 's/wifi.powersave = 3/wifi.powersave = 2/' /etc/NetworkManager/conf.d/default-wifi-powersave-on.conf
```
```
systemctl restart network-manager.service
```

Post results for ```
cat /etc/lsb-release
```

Thanks for the help.  I screwed up and said 17.10 while I meant 17.04.  I was between 16.10 and 17.04 awhile ago and got confused.  

I changed the powersave to 2 and re-ran the iperf test and still am receiving the 12Mbit/sec.

```
foo@lucy:/etc/NetworkManager/conf.d$ iperf -c 10.0.112.1
------------------------------------------------------------
Client connecting to 10.0.112.1, TCP port 5001
TCP window size: 85.0 KByte (default)
------------------------------------------------------------
[  3] local 10.0.112.73 port 46962 connected with 10.0.112.1 port 5001
[ ID] Interval       Transfer     Bandwidth
[  3]  0.0-10.0 sec  14.4 MBytes  12.0 Mbits/sec
foo@lucy:/etc/NetworkManager/conf.d$ cat /etc/lsb-release 
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=17.04
DISTRIB_CODENAME=zesty
DISTRIB_DESCRIPTION="Ubuntu 17.04"
foo@lucy:/etc/NetworkManager/conf.d$ 




```

---

