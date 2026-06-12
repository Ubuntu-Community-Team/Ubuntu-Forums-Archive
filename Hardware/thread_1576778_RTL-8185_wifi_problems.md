---
title: "RTL-8185 wifi problems"
date: 2010-09-17
forum: Hardware
---

### Post by jpr0 on 2010-09-17
As with every single wireless card I have ever put into an ubuntu machine, I'm experiencing problems with the wireless card. 

The machine is about 3 metres away from the wireless router and the signal strength is 15%. 

I'm using a realtek RTL-8185 card: 

```
robinsjp@robinsjp-desktop:~$ lspci | grep Realtek
03:06.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8185 IEEE 802.11a/b/g Wireless LAN Controller (rev 20)
```

wlanconfig shows me this: 

```
wlan0     IEEE 802.11bg  ESSID:"eTec"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:13:64:3B:24:FF   
          Bit Rate=54 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=14/100  Signal level=14/100  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

I've tried downloading the windows XP driver for the RTL-8185 card from the realtek website found [here]("http://www.realtek.com/downloads/downloadsView.aspx?Langid=1&PNid=1&PFid=1&Level=6&Conn=5&DownTypeID=3&GetDown=false&Downloads=true#RTL8187L"), and using ndiswrapper: 

```
ndiswrapper -l
WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.
net8185 : driver installed
	device (10EC:8185) present (alternate driver: rtl8180)

```

I've then tried 

```
sudo rmmod rtl8180 
robinsjp@robinsjp-desktop:~$ sudo modprobe ndiswrapper 
WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.
```

...and the wireless doesn't reappear.... 

```
iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

```

From /var/log/messages I see that ndiswrapper couldn't load the driver: 

```
Sep 18 01:40:24 robinsjp-desktop kernel: [  649.516393] rtl8180 0000:03:06.0: PCI INT A disabled
Sep 18 01:40:27 robinsjp-desktop kernel: [  653.008059] ndiswrapper version 1.55 loaded (smp=yes, preempt=no)
Sep 18 01:40:27 robinsjp-desktop loadndisdriver: loadndisdriver: load_driver(358): couldn't load driver net8185
Sep 18 01:40:27 robinsjp-desktop kernel: [  653.044205] usbcore: registered new interface driver ndiswrapper

```

Does anyone know how to get this chipset working? I'm using ubuntu 10.04 with the 2.6.32-25-generic kernel. The rtl module is: 

```
robinsjp@robinsjp-desktop:~$ modinfo rtl8180 
filename:       /lib/modules/2.6.32-25-generic/kernel/drivers/net/wireless/rtl818x/rtl8180.ko
license:        GPL
description:    RTL8180 / RTL8185 PCI wireless driver
author:         Andrea Merello <andreamrl@tiscali.it>
author:         Michael Wu <flamingice@sourmilk.net>
srcversion:     ADF1CC74E82DC7AC0ACB656
alias:          pci:v00001186d00003300sv*sd*bc*sc*i*
alias:          pci:v00001799d00006020sv*sd*bc*sc*i*
alias:          pci:v00001799d00006001sv*sd*bc*sc*i*
alias:          pci:v000010ECd00008180sv*sd*bc*sc*i*
alias:          pci:v00001799d0000701Fsv*sd*bc*sc*i*
alias:          pci:v00001799d0000700Fsv*sd*bc*sc*i*
alias:          pci:v000010ECd00008185sv*sd*bc*sc*i*
depends:        mac80211,eeprom_93cx6,cfg80211
vermagic:       2.6.32-25-generic SMP mod_unload modversions 586 

```

Any help would be appreciated.

---

### Post by damatta on 2010-09-20
The signal strength is low because of the driver. I had to blacklist the default driver and compile realtek's linux version. But  my connection still very unstable

---

### Post by jpr0 on 2010-09-20
> **damatta said:**
> The signal strength is low because of the driver. I had to blacklist the default driver and compile realtek's linux version. But  my connection still very unstable

Yeah I figured it was a driver issue, which is why I was trying to use the windows driver with ndiswrapper. Ndiswrapper doesn't work either though.

---

### Post by jpr0 on 2010-09-20
Instead of using the drivers found from the Realtek page, I used the drivers provided by the makers of this card (in my case this happens to be tp-link), the driver page for that card is [here]("http://www.tp-link.com/support/download.asp?a=1&m=TL-WN353G"). 

Using those drivers in ndiswrapper works. I wonder why those drivers should work and the ones provided by Realtek not? The only difference I can see is that the .inf file is different (I haven't checked the contents, but the file name is different), but the .sys file seems to be the same for both.

In short, the ``solution'' is this: go to the website of the card manufacturer, rather than the chipset manufacturer, and download the drivers for your card. Use ndiswrapper to load the driver. 

This worked for me, I now get 98% signal strength.

---

### Post by damatta on 2010-09-20
I'll try that too, my connection still very unstable although the signal is great.

One question: are you using ubuntu x64?

---

### Post by jpr0 on 2010-09-20
> **damatta said:**
> I'll try that too, my connection still very unstable although the signal is great.

One question: are you using ubuntu x64?

No, I'm using the 32-bit version.

---

