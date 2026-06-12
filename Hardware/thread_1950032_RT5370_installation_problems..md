---
title: "RT5370 installation problems."
date: 2012-03-31
forum: Hardware
---

### Post by kammce on 2012-03-31
Ubuntu 10.04LTS
2.6.32-37-generic
x86_64 GNU/Linux

I am attempting to use a TP-Link TLWN727N wireless N USB Adapter with the RT5370 driver. When I attempt to insert this module I get:

```

~/Documents/drivers/RaLink/RT5370$ sudo modprobe rt5370sta
FATAL: Error inserting rt5370sta (/lib/modules/2.6.32-37-generic/kernel/drivers/net/wireless/rt5370sta.ko): Unknown symbol in module, or unknown parameter (see dmesg)

```

My dmesg shows:
```

[   18.435950] usb 3-2: usbfs: interface 1 claimed by usblp while 'usb' sets config #1
[   21.441809] usb 3-2: usbfs: interface 1 claimed by usblp while 'usb' sets config #1
[  161.722785] rt5370sta: Unknown symbol usb_alloc_urb
[  161.722955] rt5370sta: Unknown symbol usb_free_urb
[  161.723457] rt5370sta: Unknown symbol usb_register_driver
[  161.723826] rt5370sta: Unknown symbol usb_put_dev
[  161.723961] rt5370sta: Unknown symbol usb_get_dev
[  161.724212] rt5370sta: Unknown symbol usb_submit_urb
[  161.724862] rt5370sta: Unknown symbol usb_control_msg
[  161.725281] rt5370sta: Unknown symbol usb_deregister
[  161.725914] rt5370sta: Unknown symbol usb_kill_urb
[  161.726043] rt5370sta: Unknown symbol usb_buffer_free
[  161.726624] rt5370sta: Unknown symbol usb_buffer_alloc

```

Did I miss something when I compiled these drivers? I did the normal 
```

sudo su
# I had to use 'make clean' because I accidently compiled without admin privileges. 
make clean 
make
make install
modprobe rt5370sta
exit

```
Is this a problem with the driver? Is my kernel missing some of the symbol/objects that were stated in my kernel logs? Is there anyway to fix this?

---

### Post by wnelson on 2012-03-31
Could you provide the output for you usb devices, lsusb.

You may want to see if rt3070 is available.

If not:

Here are the following drivers.

[http://www.ralinktech.com/en/04_support/support.php?sn=501](http://www.ralinktech.com/en/04_support/support.php?sn=501)


Walt

---

### Post by kammce on 2012-03-31
```

~/Documents/drivers/RaLink/RT5370$ lsusb
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 003: ID 148f:5370 Ralink Technology, Corp. 
Bus 003 Device 002: ID 03f0:8911 Hewlett-Packard 
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 050d:705c Belkin Components 802.11bg
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

```

I will see if those other drivers work.

---

### Post by kammce on 2012-03-31
Ok! I installed the RT3070 drivers.
lsmod shows:
```

lsmod
Module                  Size  Used by
rt5370sta             794186  0 

```
With absolutley no errors. dmesg shows:
```

[ 8277.174066] usbcore: registered new interface driver rt2870
[ 8292.070021] usb 3-1: new full speed USB device using uhci_hcd and address 4
[ 8292.255449] usb 3-1: configuration #1 chosen from 1 choice
[ 8292.266345] 
[ 8292.266347] 
[ 8292.266348] === pAd = ffffc9001413c000, size = 549456 ===
[ 8292.266349] 
[ 8292.266656] <-- RTMPAllocTxRxRingMemory, Status=0
[ 8292.266752] <-- RTMPAllocAdapterBlock, Status=0
[ 8328.521304] wlan0: deauthenticating from 00:14:6c:04:62:af by local choice (reason=3)
[ 8336.540073] usb 2-1: USB disconnect, address 2
[ 8381.265634] (Efuse for 3062/3562/3572) Size=0x2d [2d0-2fc] 
[ 8383.322796] RTMP_TimerListAdd: add timer obj ffffc90014185018!
[ 8383.322802] RTMP_TimerListAdd: add timer obj ffffc90014185090!
[ 8383.322805] RTMP_TimerListAdd: add timer obj ffffc90014185108!
[ 8383.322809] RTMP_TimerListAdd: add timer obj ffffc90014184fa0!
[ 8383.322814] RTMP_TimerListAdd: add timer obj ffffc90014184e38!
[ 8383.322817] RTMP_TimerListAdd: add timer obj ffffc90014184eb0!
[ 8383.322820] RTMP_TimerListAdd: add timer obj ffffc9001414f320!
[ 8383.322824] RTMP_TimerListAdd: add timer obj ffffc9001413e668!
[ 8383.322827] RTMP_TimerListAdd: add timer obj ffffc9001413e6e8!
[ 8383.322830] RTMP_TimerListAdd: add timer obj ffffc9001414f4b0!
[ 8383.322835] RTMP_TimerListAdd: add timer obj ffffc9001414f230!
[ 8383.322839] RTMP_TimerListAdd: add timer obj ffffc9001414f430!
[ 8383.333570] -->RTUSBVenderReset
[ 8383.334569] <--RTUSBVenderReset
[ 8387.277472] Key1Str is Invalid key length(0) or Type(0)
[ 8387.277528] Key2Str is Invalid key length(0) or Type(0)
[ 8387.277585] Key3Str is Invalid key length(0) or Type(0)
[ 8387.277643] Key4Str is Invalid key length(0) or Type(0)
[ 8387.278821] 1. Phy Mode = 5
[ 8387.278824] 2. Phy Mode = 5
[ 8387.278827] NVM is Efuse and its size =2d[2d0-2fc] 
[ 8387.677442] phy mode> Error! The chip does not support 5G band 15!
[ 8387.677553] RTMPSetPhyMode: channel is out of range, use first channel=1 
[ 8387.707440] (Efuse for 3062/3562/3572) Size=0x2d [2d0-2fc] 
[ 8387.877438] 3. Phy Mode = 9
[ 8387.897436] AntCfgInit: primary/secondary ant 0/1
[ 8387.897438] AsicSetRxAnt, switch to main antenna
[ 8388.210431] MCS Set = ff 00 00 00 01
[ 8388.226458] <==== rt28xx_init, Status=0
[ 8388.239423] 0x1300 = 00064300
[ 8399.160010] ra0: no IPv6 routers present
[ 8851.964047] ERROR!!! RTMPSetTimer failed, Halt in Progress!

```
The light on the device has turned on, but I do not know how to get it to connect to the internet.
```

iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

vboxnet0  no wireless extensions.

ra0       Ralink STA  
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  invalid crypt:0  invalid misc:0

wlan0     IEEE 802.11bg  ESSID:"[hidden]"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:14:6C:04:62:AF   
          Bit Rate=1 Mb/s   Tx-Power=27 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=28/100  Signal level=28/100  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```
ra0 is blank. ifconfig shows:
```

ifconfig
eth0      Link encap:Ethernet  HWaddr 00:24:21:b6:22:10  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:27 Base address:0x2000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:3518 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3518 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:291135 (291.1 KB)  TX bytes:291135 (291.1 KB)

wlan0     Link encap:Ethernet  HWaddr 00:17:3f:b2:2b:7b  
          inet addr:[hidden]  Bcast:192.168.15.255  Mask:255.255.255.0
          inet6 addr: fe80::217:3fff:feb2:2b7b/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1111 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1257 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:756548 (756.5 KB)  TX bytes:232097 (232.0 KB)

```

Do not worry about the wlan0 interface. I am using another USB dongle to get access to the internet. How do I "ifconfig ra0 up"?

---

### Post by kammce on 2012-03-31
Lol, nevermind I got it to work.

I found a script online that will set it up for me. Here it is if anyone needs it!

```

ifconfig ra0 up

sleep 1

iwpriv ra0 set WirelessMode=Managed
# next line sets authentication mode, this should match your routed options are: #OPEN,SHARED,WEPAUTO,WPAPSK,WPA2PSK,WPANONE
iwpriv ra0 set AuthMode=WEPAUTO
# next line sets the encryption type, this should match your router setup options are; NONE,WEP,TKIP,AES
iwpriv ra0 set EncrypType=WEP
#set SSID = "your wireless SSID" no quotes
iwpriv ra0 set SSID="your wireless SSID"
# set your wireless pass word by setting WPAPSK=" your wireless password" no quotes
iwpriv ra0 set WPAPSK=" your wireless password"
# trust me.
sleep 1

# I like dhcp.
dhcpcd ra0

```
what I noticed about this program is that Ubuntu 10.04LTS does not have the program 'dhcpcd' but it will still work without... I might just make a tutorial on how to get this device to work! 

:D

---

