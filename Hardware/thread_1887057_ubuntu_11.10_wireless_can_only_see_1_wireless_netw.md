---
title: "ubuntu 11.10 wireless can only see 1 wireless network"
date: 2011-11-26
forum: Hardware
---

### Post by Ahmed Kotb on 2011-11-26
Hi,
i have just installed 11.10 x64 on my laptop

the problem is it doesn't see my wireless network , it can only see one of the neighbors networks (not even all the other networks)

i can't test if it was able to connect as this network is secured

i installed the network driver from the additional drivers dialog as ubuntu suggested
the output of the following command lspci -nvn | grep -i net

```
04:00.0 Network controller [0280]: Broadcom Corporation BCM4313 802.11b/g/n Wireless LAN Controller [14e4:4727] (rev 01)
05:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 05)

```


the output for iwconfig is
```

lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=19 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off

```


when i try this command to scan networks i get nothing
```

sudo iwlist wlan0 scanning
wlan0     No scan results

```

---

### Post by kurt18947 on 2011-11-26
Excuse me if this is obvious but is your network SSID hidden?

---

### Post by Ahmed Kotb on 2011-11-26
> **kurt18947 said:**
> Excuse me if this is obvious but is your network SSID hidden?

no , the access point is not hidden , i can connect to it directly through many devices at home

i have removed 11.10 and installed 10.04 but the same problem occurs exactly
only 1 network (which is not mine ) is seen using the iwlist command

any help will be appreciated

---

### Post by Ahmed Kotb on 2011-11-27
Hi after alot of searching i was able to fix it using instructions in this link
[http://tuxcanfly.appspot.com/2011/10/Ubuntu-11-10-Broadcom-Wifi-driver-43xx](http://tuxcanfly.appspot.com/2011/10/Ubuntu-11-10-Broadcom-Wifi-driver-43xx)

brcmsmac is the reason for all this problems , the solution was to blacklist it and install bcmwl-kernel-source

hope that helps

thanks

---

