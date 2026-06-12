---
title: "Flakey Wireless - 10.04 - PRO/Wireless 5100 AGN"
date: 2010-09-20
forum: Hardware
---

### Post by tbastian on 2010-09-20
My girlfriend has a HP Pavillion dv5, and I installed 10.04 on it for her. She LOVES linux, but currently her wireless is a little flakey. It comes up, and she can see and connect to networks, but sometimes the internet won't work.

I've deduced this is definitely a wireless issue, because everyone else in her house can connect just fine with their windows machines, and when she gets a wired plugin, it works just fine too.

Here is the output of some important commands:

```
:~$ lshw -C Network 
WARNING: you should run this program as super-user. 
  *-network               
       description: Wireless interface 
       product: PRO/Wireless 5100 AGN [Shiloh] Network Connection 
       vendor: Intel Corporation 
       physical id: 0 
       bus info: pci@0000:02:00.0 
       logical name: wlan1 
       version: 00 
       serial: 00:22:fa:53:b1:ce 
       width: 64 bits 
       clock: 33MHz 
       capabilities: bus_master cap_list ethernet physical wireless 
       configuration: broadcast=yes driver=iwlagn ip=192.168.1.106 latency=0 multicast=yes wireless=IEEE 802.11abgn 
       resources: irq:32 memory:db600000-db601fff 
  *-network 
       description: Ethernet interface 
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller 
       vendor: Realtek Semiconductor Co., Ltd. 
       physical id: 0 
       bus info: pci@0000:03:00.0 
       logical name: eth2 
       version: 02 
       serial: 00:23:8b:79:c5:01 
       width: 64 bits 
       clock: 33MHz 
       capabilities: bus_master cap_list rom ethernet physical 
       configuration: broadcast=yes driver=r8169 driverversion=2.3LK-NAPI latency=0 multicast=yes 
       resources: irq:30 ioport:6000(size=256) memory:d1410000-d1410fff(prefetchable) memory:d1400000-d140ffff(prefetchable) memory:d1420000-d142ffff(prefetchable)
```

```

:~$ dmesg | grep -i wlan 
[   16.135229] udev: renamed network interface wlan0 to wlan1 
[   17.392898] ADDRCONF(NETDEV_UP): wlan1: link is not ready 
[   33.642438] wlan1: deauthenticating from 00:21:29:ab:40:5b by local choice (reason=3) 
[   33.642772] wlan1: direct probe to AP 00:21:29:ab:40:5b (try 1) 
[   33.840041] wlan1: direct probe to AP 00:21:29:ab:40:5b (try 2) 
[   34.040071] wlan1: direct probe to AP 00:21:29:ab:40:5b (try 3) 
[   34.044724] wlan1: direct probe responded 
[   34.044727] wlan1: authenticate with AP 00:21:29:ab:40:5b (try 1) 
[   34.048279] wlan1: authenticated 
[   34.048297] wlan1: associate with AP 00:21:29:ab:40:5b (try 1) 
[   34.055135] wlan1: RX AssocResp from 00:21:29:ab:40:5b (capab=0x411 status=0 aid=4) 
[   34.055137] wlan1: associated 
[   34.056635] ADDRCONF(NETDEV_CHANGE): wlan1: link becomes ready 
[   44.980031] wlan1: no IPv6 routers present 

```

```

:~$ modinfo iwlagn 
filename:       /lib/modules/2.6.32-24-generic/kernel/drivers/net/wireless/iwlwifi/iwlagn.ko 
alias:          iwl4965 
license:        GPL 
author:         Copyright(c) 2003-2009 Intel Corporation <ilw@linux.intel.com> 
version:        1.3.27k 
description:    Intel(R) Wireless WiFi Link AGN driver for Linux 
firmware:       iwlwifi-4965-2.ucode 
firmware:       iwlwifi-5150-2.ucode 
firmware:       iwlwifi-5000-2.ucode 
firmware:       iwlwifi-6050-4.ucode 
firmware:       iwlwifi-6000-4.ucode 
srcversion:     BB501FCC68D0C8213107D3B 
alias:          pci:v00008086d00000084sv*sd*bc*sc*i* 
alias:          pci:v00008086d00000083sv*sd*bc*sc*i* 
alias:          pci:v00008086d00000089sv*sd*bc*sc*i* 
alias:          pci:v00008086d00000088sv*sd*bc*sc*i* 
alias:          pci:v00008086d00000087sv*sd*bc*sc*i* 
alias:          pci:v00008086d00000086sv*sd*bc*sc*i* 
alias:          pci:v00008086d00004239sv*sd*bc*sc*i* 
alias:          pci:v00008086d00004238sv*sd*bc*sc*i* 
alias:          pci:v00008086d0000422Csv*sd*bc*sc*i* 
alias:          pci:v00008086d0000422Bsv*sd*bc*sc*i* 
alias:          pci:v00008086d0000008Esv*sd*bc*sc*i* 
alias:          pci:v00008086d0000008Dsv*sd*bc*sc*i* 
alias:          pci:v00008086d0000423Dsv*sd*bc*sc*i* 
alias:          pci:v00008086d0000423Csv*sd*bc*sc*i* 
alias:          pci:v00008086d0000423Bsv*sd00001011bc*sc*i* 
alias:          pci:v00008086d0000423Asv*sd00001021bc*sc*i* 
alias:          pci:v00008086d0000423Asv*sd00001001bc*sc*i* 
alias:          pci:v00008086d00004237sv*sd*bc*sc*i* 
alias:          pci:v00008086d00004236sv*sd*bc*sc*i* 
alias:          pci:v00008086d00004235sv*sd*bc*sc*i* 
alias:          pci:v00008086d00004232sv*sd*bc*sc*i* 
alias:          pci:v00008086d00004237sv*sd00001216bc*sc*i* 
alias:          pci:v00008086d00004232sv*sd00001326bc*sc*i* 
alias:          pci:v00008086d00004232sv*sd00001306bc*sc*i* 
alias:          pci:v00008086d00004232sv*sd00001206bc*sc*i* 
alias:          pci:v00008086d00004232sv*sd00001305bc*sc*i* 
alias:          pci:v00008086d00004232sv*sd00001205bc*sc*i* 
alias:          pci:v00008086d00004230sv*sd*bc*sc*i* 
alias:          pci:v00008086d00004229sv*sd*bc*sc*i* 
depends:        iwlcore,mac80211,cfg80211 
vermagic:       2.6.32-24-generic SMP mod_unload modversions 
parm:           swcrypto50:using software crypto engine (default 0 [hardware]) 
 (bool) 
parm:           queues_num50:number of hw queues in 50xx series (int) 
parm:           11n_disable50:disable 50XX 11n functionality (int) 
parm:           amsdu_size_8K50:enable 8K amsdu size in 50XX series (int) 
parm:           fw_restart50:restart firmware in case of error (int) 
parm:           antenna:select antenna (1=Main, 2=Aux, default 0 [both]) (int) 
parm:           swcrypto:using crypto in software (default 0 [hardware]) (int) 
parm:           disable_hw_scan:disable hardware scanning (default 0) (int) 
parm:           queues_num:number of hw queues. (int) 
parm:           11n_disable:disable 11n functionality (int) 
parm:           amsdu_size_8K:enable 8K amsdu size (int) 
parm:           fw_restart4965:restart firmware in case of error (int) 
```

```

eth2      Link encap:Ethernet  HWaddr 00:23:8b:79:c5:01  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1 
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B) 
          Interrupt:30 Base address:0x6000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0 
          inet6 addr: ::1/128 Scope:Host 
          UP LOOPBACK RUNNING  MTU:16436  Metric:1 
          RX packets:27 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:27 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:0 
          RX bytes:3050 (3.0 KB)  TX bytes:3050 (3.0 KB) 

wlan1     Link encap:Ethernet  HWaddr 00:22:fa:53:b1:ce  
          inet addr:192.168.1.106  Bcast:192.168.1.255  Mask:255.255.255.0 
          inet6 addr: fe80::222:faff:fe53:b1ce/64 Scope:Link 
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1 
          RX packets:4717 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:3081 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:1000 
          RX bytes:5272112 (5.2 MB)  TX bytes:461006 (461.0 KB) 

```

In my opinion, the output of modinfo and dmesg could be cause for concern. Does anybody have any ideas?

---

### Post by tbastian on 2010-09-21
bump

---

### Post by tbastian on 2010-09-21
What do people think of ndiswrapper?

---

### Post by svega85 on 2010-10-17
This is a current intel firmware bug, I have the same problem :( 
[https://bugs.launchpad.net/ubuntu/+source/linux-firmware/+bug/630748](https://bugs.launchpad.net/ubuntu/+source/linux-firmware/+bug/630748)

---

### Post by sritacco on 2010-10-18
If it is an Intel firmware issue, why was it not happening for me in 10.04 but then after
the 10.10 upgrade it is happening?

---

### Post by svega85 on 2010-10-19
> **sritacco said:**
> If it is an Intel firmware issue, why was it not happening for me in 10.04 but then after
the 10.10 upgrade it is happening?

The firmware is called ucode, it gets loaded by the driver on to the card every time you boot up. when the driver gets updated sometimes they update the ucode. the current version of ucode has been haveing issues with the latest release of linux which got upgraded when you upgraded ubuntu.

---

### Post by svega85 on 2010-10-19
@tbastian are you using 802.11n? because this issue seems to be mostly affecting 802.11n users. if you are, you might want to try switching to 802.11g

---

### Post by tbastian on 2010-10-19
> **svega85 said:**
> @tbastian are you using 802.11n? because this issue seems to be mostly affecting 802.11n users. if you are, you might want to try switching to 802.11g

I have to admit I have no idea what you're talking about... How would I switch?

---

### Post by svega85 on 2010-10-20
> **tbastian said:**
> I have to admit I have no idea what you're talking about... How would I switch?

what kind of router do you use?

---

### Post by tbastian on 2010-10-20
linksys cisco wireless-n

---

### Post by svega85 on 2010-10-22
> **tbastian said:**
> linksys cisco wireless-n
you need to go to your router setting which should be at [http://192.168.1.1](http://192.168.1.1) from ther type in your user name (admin) and password. then go to the wireless tab and change it to G only.

---

