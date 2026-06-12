---
title: "Intel WiFi Link 5100 AGN cannot connect to N networks"
date: 2011-03-06
forum: Hardware
---

### Post by Schadenfroh on 2011-03-06
Hardware 
Intel Wifi Link 5100
[http://www.intel.com/Assets/PDF/prodbrief/319981.pdf]("Intel Documentation")

Router:  Asus RT-n16
Tested with both Tomato USB (Teddy Bear) and currently using DD-WRT Big build 14929 (latest recommended build for this router), set to N only.


Software
Operating System:  Ubuntu 10.10 x64 (fresh install)
uname -a:
> Linux SchadenBook 2.6.35-27-generic #48-Ubuntu SMP Tue Feb 22 20:25:46 UTC 2011 x86_64 GNU/Linux

lshw -C network
> *-network
       description: Wireless interface
       product: PRO/Wireless 5100 AGN [Shiloh] Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wlan0
       version: 00
       serial: 00:22:fa:c3:d7:7c
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwlagn driverversion=2.6.35-27-generic firmware=8.24.2.12 latency=0 link=no multicast=yes wireless=IEEE 802.11abg
       resources: irq:47 memory:f4200000-f4201fff


iwconfig:
> lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11abg  ESSID:"SchadenNet"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: Not-Associated   
          Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off

ifconfig:
> wlan0     Link encap:Ethernet  HWaddr 00:22:fa:c3:d7:7c  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

dmesg:
>    12.451551] iwlagn: Intel(R) Wireless WiFi Link AGN driver for Linux, in-tree:
[   12.451553] iwlagn: Copyright(c) 2003-2010 Intel Corporation
[   12.451641] iwlagn 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   12.451670] iwlagn 0000:03:00.0: setting latency timer to 64
[   12.451772] iwlagn 0000:03:00.0: Detected Intel(R) WiFi Link 5100 AGN, REV=0x54
[   12.475313] iwlagn 0000:03:00.0: Tunable channels: 13 802.11bg, 24 802.11a channels
[   12.475453] iwlagn 0000:03:00.0: irq 47 for MSI/MSI-X
[   12.519466] iwlagn 0000:03:00.0: loaded firmware version 8.24.2.12
[   12.526599] phy0: Selected rate control algorithm 'iwl-agn-rs'


 ls -l /lib/firmware | grep iwl:
> 
-rw-r--r--  1 root root  335056 2010-12-13 15:01 iwlwifi-1000-3.ucode
-rw-r--r--  1 root root  150100 2010-12-13 15:01 iwlwifi-3945-2.ucode
-rw-r--r--  1 root root  187972 2010-12-13 15:01 iwlwifi-4965-2.ucode
-rw-r--r--  1 root root  345008 2010-12-13 15:01 iwlwifi-5000-1.ucode
-rw-r--r--  1 root root  353240 2010-12-13 15:01 iwlwifi-5000-2.ucode
-rw-r--r--  1 root root  337400 2010-12-13 15:01 iwlwifi-5150-2.ucode
-rw-r--r--  1 root root  454608 2010-12-13 15:01 iwlwifi-6000-4.ucode
-rw-r--r--  1 root root  444128 2011-02-11 09:20 iwlwifi-6000g2a-5.ucode
-rw-r--r--  1 root root  460912 2011-02-11 09:20 iwlwifi-6000g2b-5.ucode
-rw-r--r--  1 root root  463692 2011-02-11 09:17 iwlwifi-6050-4.ucode
-rw-r--r--  1 root root  469780 2010-12-14 11:18 iwlwifi-6050-5.ucode

I know the hardware and router are both fine as I dual boot with Windows 7 x64 and it connects perfectly to my N network under Windows.  

I can connect to it just fine using 802.11 G in Ubuntu 10.10 x64, but it refuses to connect using N and just keeps trying.

I suspect that the driver for Ubuntu 10.10 does not support wireless N, although I do not know how to resolve this if this is the case.

I am not familiar with loading drivers in Linux.  I tried, per the Intel readme file, copying the latest driver from [http://www.intellinuxwireless.org/](http://www.intellinuxwireless.org/) into /lib/firmware and restarting, but I think there is likely more to it than that as it did not resolve it, so I removed it.

Any thoughts on how to correct this or if I should report it as a bug?

Thanks

---

### Post by scarey9 on 2011-03-06
I received my Panp7 a weeks ago and when i tried to use it with my brand new Linksys E4200(awesome) it would not connect to my 802.11n network. It seems that wireless n was disabled. 

after editing this config file all was set as it should be. However i still have reception issues at 5ghz. 

/etc/modprobe.d/intel-5300-iwlagn-disable11n.conf

```
sudo gedit intel-5300-iwlagn-disable11n.conf
```

edit the only line from
```
options iwlagn 11n_disable=1
```
to
```
options iwlagn 11n_disable=0
```

---

### Post by Schadenfroh on 2011-03-06
scarey9,

Changing that value did the trick, I am able to connect to my network via N now.  Thanks!

---

### Post by maxpoweron on 2011-03-17
Scarey9,

Want to thanks for your post on editing the config file.  I purchased the Linksys E4200 yesterday and was having problems with wireless N too.  One think I noticed is my speed will fluctuate as I use the PC.  The lowest I saw 1Mb/s and as high as 300Mb/s.  My guess it is the 5GHz and something to do with the Intel 5300 AGN card.

Either way, thanks for the info at least I can now use most of the capabilities of the E4200.

---

