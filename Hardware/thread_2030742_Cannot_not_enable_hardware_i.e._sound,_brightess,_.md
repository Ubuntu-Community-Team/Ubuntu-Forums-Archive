---
title: "Cannot not enable hardware i.e. sound, brightess, wireless"
date: 2012-07-21
forum: Hardware
---

### Post by uk2 on 2012-07-21
Hello,

```
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=10.04
DISTRIB_CODENAME=lucid
DISTRIB_DESCRIPTION="Ubuntu 10.04.3 LTS"

HP Mini 210 x86_64

Kernel 3.2.6
```
	
I cannot enable my wireless by using the function key.

And most importantly I cannot enable my wireless. It should turn blue when I click on it (fn f12), but it remains red.

My my HP Mini, I also have Fedora 17 on a separate partition. When I boot I can activate the using the fn keys wireless.

Everything seems to be ok with loading the modules, fireware, etc.

lspci
```
01:00.0 Network controller: Broadcom Corporation BCM4313 802.11b/g/n Wireless LAN Controller (rev 01)
```

lspci -c network
```
***-**network DISABLED****      
       description: Wireless interface
       product: BCM4313 802.11b/g/n Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: wlan0
       version: 01
       serial: 70:f3:95:b4:4a:19
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=brcmsmac driverversion=3.2.6 firmware=N/A latency=0 link=no multicast=yes wireless=IEEE 802.11bgn
       resources: irq:16 memory:95000000-95003fff
```

iwconfig
```
wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=off   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:on
```

ls -l /lib/firmware/brcm/
```
bcm4329-fullmac-4.bin
bcm4329-fullmac-4.txt
bcm43xx-0.fw
bcm43xx_hdr-0.fw
```


lsmod | grep brcmsmac
```
brcmsmac              563429  0 
mac80211              478885  1 brcmsmac
brcmutil               14361  1 brcmsmac
cfg80211              190023  2 brcmsmac,mac80211
crc8                   12708  1 brcmsmac
cordic                 12486  1 brcmsmac
```

Everything looks ok, but I think I am just having trouble with switching it on.

Many thanks for any suggestions,

---

