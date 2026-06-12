---
title: "HOWTO Allnet ALL0283 USB wlan adapter with AR5523"
date: 2009-05-24
forum: Hardware
---

### Post by --dtk on 2009-05-24
Hi guys,

since the driver situation for above USB adapter has been less than perfect so far, I just wanted to quickly put down how I managed to get it working today using ndiswrapper.

[LIST=0]
[*]Downloaded the necessary Windooze Vista drivers from [http://www.allnet.de/](http://www.allnet.de/) [0] and unpacked the .zip
```

dtk@atmc31: ~/ALL0282_VISTA $> unzip ALL0283_Driver_Vista.zip 
Archive:  ALL0283_Driver_Vista.zip
  inflating: ar5523.bin              
  inflating: ar5523.sys              
  inflating: net5523.inf             
dtk@atmc31: ~/ALL0283_VISTA $> ls -AhlF
total 524K
-rw-r--r-- 1 dtk dtk 146K 2005-07-27 21:15 ar5523.bin
-rw-r--r-- 1 dtk dtk 352K 2006-01-05 16:56 ar5523.sys
-rw-r--r-- 1 dtk dtk  13K 2006-01-06 19:00 net5523.inf
dtk@atmc31: ~$>

```

[*]Installed the driver:
```

root@atmc31: ~ $> ndiswrapper -l
root@atmc31: ~ $> ndiswrapper -i ALL0283_VISTA/net5523.inf 
installing net5523 ...
forcing parameter MapRegisters from 256 to 64
forcing parameter MapRegisters from 256 to 64
forcing parameter MapRegisters from 256 to 64
forcing parameter MapRegisters from 256 to 64
forcing parameter MapRegisters from 256 to 64
forcing parameter MapRegisters from 256 to 64
forcing parameter MapRegisters from 256 to 64
forcing parameter MapRegisters from 256 to 64
root@atmc31: ~ $> ndiswrapper -l
net5523 : driver installed
	device (0CF3:0002) present
root@atmc31: ~ $> 

```

[*]Inserted the kernel module:
```

root@atmc31: ~ $> ifconfig wlan0
wlan0: error fetching interface information: Device not found
root@atmc31: ~ $> modprobe ndiswrapper
root@atmc31: ~ $> ifconfig wlan0
wlan0     Link encap:Ethernet  HWaddr 00:0f:c9:02:78:30  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
root@atmc31: ~ $> dmesg | tail
[394828.768196] usb 5-5: new high speed USB device using ehci_hcd and address 6
[394828.954511] usb 5-5: configuration #1 chosen from 1 choice
[394842.384293] ndiswrapper version 1.53 loaded (smp=yes, preempt=no)
[394842.516052] usb 5-5: reset high speed USB device using ehci_hcd and address 6
[394842.653649] ndiswrapper: driver net5523 (,07/27/2005,1.5.0.102) loaded
[394842.656198] ndiswrapper (ZwQueryValueKey:2330): not fully implemented (yet)
[394843.315590] wlan0: ethernet device 00:0f:c9:02:78:30 using NDIS driver: net5523, version: 0x10005, NDIS version: 0x501, vendor: 'NDIS Network Adapter', 0CF3:0002.F.conf
[394843.393629] wlan0: encryption modes supported: WEP; TKIP with WPA, WPA2, WPA2PSK; AES/CCMP with WPA, WPA2, WPA2PSK
[394843.394289] usbcore: registered new interface driver ndiswrapper
[394847.446689] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[395056.971442] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
root@atmc31: ~ $> 

```
[*]I then connected the adapter to the local WPA encrypted network following this[1] tutorial. Worked like a charm. Thx to the author!
[/LIST]



_Troubleshooting_
[LIST]
[*]Originally I installed the adapter on an Xubuntu 8.10:
```

dtk@atmc31: ~ $> uname -a
Linux atmc31 2.6.27-14-generic #1 SMP Wed Apr 15 18:59:16 UTC 2009 i686 GNU/Linux
dtk@atmc31: ~ $> ndiswrapper -v
utils version: '1.9', utils version needed by module: '1.9'
module details:
filename:       /lib/modules/2.6.27-14-generic/kernel/ubuntu/ndiswrapper/ndiswrapper.ko
version:        1.53
vermagic:       2.6.27-14-generic SMP mod_unload modversions 586 
root@atmc31:/media/dump/downloads/allnet_all0283# 

```
I successfully reproduced this procedure on my sister's notebook, running an Ubuntu 9.04:
```

pia@sami: ~ $> uname -a
Linux same 2.6.28-11-generic #42-Ubuntu SMP Fri Apr 17 01:57:59 UTC i686 GNU/Linux
pia@sami: ~ $>

```
However, sometimes there are some issues inserting the kernel module:
```

May 24 20:58:42 atmc31 kernel: [394435.857435] ndiswrapper: driver net5523 (,07/27/2005,1.5.0.102) loaded
May 24 20:58:42 atmc31 kernel: [394435.859978] ndiswrapper (ZwQueryValueKey:2330): not fully implemented (yet)
May 24 20:58:57 atmc31 kernel: [394450.922901] ndiswrapper (mp_init:219): couldn't initialize device: C0000001
May 24 20:58:57 atmc31 kernel: [394450.922919] ndiswrapper (pnp_start_device:435): Windows driver couldn't initialize the device (C0000001)
May 24 20:58:57 atmc31 kernel: [394450.922943] ndiswrapper (mp_halt:262): device c209c480 is not initialized - not halting
May 24 20:58:57 atmc31 kernel: [394450.922951] ndiswrapper: device eth%d removed
May 24 20:58:57 atmc31 kernel: [394450.927626] ndiswrapper: probe of 5-5:1.0 failed with error -22
May 24 20:58:57 atmc31 kernel: [394450.928673] usbcore: registered new interface driver ndiswrapper

```
I seem to find that this is fixed rmmodding the ndiswrapper module, un- and re-plug the USB device and then modprobing ndiswrapper again.

I have played around with (the deprecated) 
```

root@atmc31: ~ $> ndiswrapper -m
adding "alias wlan0 ndiswrapper" to /etc/modprobe.d/ndiswrapper ...

************************************************************************
*
* The update-modules command is deprecated and should not be used!
*
************************************************************************

root@atmc31: ~ $> 

```
and the module parameter
```

root@atmc31: ~ $> modprobe ndiswrapper if_name=ath%d
root@atmc31: ~ $>

```
but right now I am not quite sure whether it has a deterministic influence on the behaviour of the driver -.-
[*] Afaik, the [FONT="Courier New"]ndiswrapper -m[/FONT] command is somewhat meant to insert the ndiswrapper module on triggering the linked interface. So far, that doesn't really work. Unplugging the adapter while in use and trying to make it being recognized again may lead to a great
```

root@atmc31: ~ $> rmmod ndiswrapper 
ERROR: Module ndiswrapper is in use
root@atmc31: ~ $>

```
I am pretty sure there is an elegant solution to this fleabite, I'm just too tired now to investigate it.
[/LIST]

Despite the shortcomings of these notes, I

hth
dtk


__________
[0]http://212.18.29.49/ftp/pub/allnet/wireless/all0283/ALL0283_Driver_Vista.zip
[1]http://ubuntuforums.org/showthread.php?t=263136

---

### Post by --dtk on 2009-05-24
Just thought adding the driver for redundancy might help some day.
dtk

---

