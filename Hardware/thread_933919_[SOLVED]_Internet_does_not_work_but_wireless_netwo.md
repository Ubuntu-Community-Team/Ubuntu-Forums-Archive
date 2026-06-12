---
title: "[SOLVED] Internet does not work but wireless network detected"
date: 2008-09-29
forum: Hardware
---

### Post by flala on 2008-09-29
Hi,

I am facing a problem where I could connect to the wireless network and when I run "iwconfig" on terminal I get:

lo no wireless extensions.

eth1 no wireless extensions.

eth0 IEEE 802.11g ESSID:"TRU03"
     Mode:Managed Frequency:2.412 GHz Access Point: 00:18:01:F4:4D:07
     Bit Rate:54 Mb/s Tx-Power=20 dBm Sensitivity=8/0
     Retry Limit:7 RTS thr:off Fragment thr:off
     Power Management:off
     Link Quality=94/100 Signal level=-33 dBm Noise level=-87 dBm
     Rx invalid nwid:0 Rx invalid crypt:767 Rx invalid frag:0
     Tx excessive retries:0 Invalid misc:0 Missed beacon:0

But when I open Firefox, I get an "address not found" error. System->Administration->Network->Wireless Network Properties:
ESSID: TRU03
Password type: WEP key (ascii) (I tried all others too)
Configuration: Static IP Address/Automatic Configuration(DHCP)/Local Zeroconf (IPv4 LL)
Static IP Address: 127.0.0.1
(when I chose static IP) Subnet mask: 250.250.0.0
(when I chose Static IP) Gateway address: 192.168.1.1

And with all this, my internet does not work. Would anyone be able to help me? I'd really appreciate it.

-Fauzia

---

### Post by pytheas22 on 2008-09-30
Do you normally need to use static IP with this network?  Are you able to get an IP address when you try to connect with dhcp enabled?  If you're not sure or don't know what that means, please try to connect to the network, then post the output of:

```
ifconfig
```

Please also post:

```
iwconfig
lshw -C Network
iwlist scan
sudo iwconfig essid "TRU03" mode managed
sudo dhclient eth0
```

Also, have you tried disabling encryption on the wireless network and then connecting?  This may help.

---

### Post by flala on 2008-09-30
No I do not normally need to use static IP. I do get an IP address when I connect using dhcp. I am not sure how to disable encryption. I will look online and if I figure something out and try it, I'll post that as well. Here are the outputs of what you asked for:
 
```
 
fauzia@Fauzia:~$ ifconfig 
eth0 Link encap:Ethernet HWaddr 00:13:ce:37:5b:9e 
UP BROADCAST MULTICAST MTU:1500 Metric:1 
RX packets:11791 errors:0 dropped:0 overruns:0 frame:0 
TX packets:1383 errors:0 dropped:0 overruns:0 carrier:0 
collisions:0 txqueuelen:1000 
RX bytes:0 (0.0 B) TX bytes:0 (0.0 B) 
Interrupt:10 Base address:0x2000 Memory:e0206000-e0206fff 
 
eth1 Link encap:Ethernet HWaddr 00:12:3f:82:70:d1 
UP BROADCAST MULTICAST MTU:1500 Metric:1 
RX packets:0 errors:0 dropped:0 overruns:0 frame:0 
TX packets:0 errors:0 dropped:0 overruns:0 carrier:0 
collisions:0 txqueuelen:1000 
RX bytes:0 (0.0 B) TX bytes:0 (0.0 B) 
Interrupt:10 
 
lo Link encap:Local Loopback 
inet addr:127.0.0.1 Mask:255.0.0.0 
inet6 addr: ::1/128 Scope:Host 
UP LOOPBACK RUNNING MTU:16436 Metric:1 
RX packets:1490 errors:0 dropped:0 overruns:0 frame:0 
TX packets:1490 errors:0 dropped:0 overruns:0 carrier:0 
collisions:0 txqueuelen:0 
RX bytes:74500 (72.7 KB) TX bytes:74500 (72.7 KB) 
 
fauzia@Fauzia:~$ iwconfig 
lo no wireless extensions. 
 
eth1 no wireless extensions. 
 
eth0 unassociated ESSID:"TRUO3" 
Mode:Managed Channel=0 Access Point: Not-Associated 
Bit Rate:0 kb/s Tx-Power=20 dBm Sensitivity=8/0 
Retry limit:7 RTS thr:off Fragment thr:off 
Power Management:off 
Link Quality:0 Signal level:0 Noise level:0 
Rx invalid nwid:0 Rx invalid crypt:0 Rx invalid frag:0 
Tx excessive retries:0 Invalid misc:0 Missed beacon:0 
 
fauzia@Fauzia:~$ lshw -C network 
WARNING: you should run this program as super-user. 
*-network:0 
description: Wireless interface 
product: PRO/Wireless 2200BG Network Connection 
vendor: Intel Corporation 
physical id: 1 
bus info: pci@0000:02:01.0 
logical name: eth0 
version: 05 
serial: 00:13:ce:37:5b:9e 
width: 32 bits 
clock: 33MHz 
capabilities: bus_master cap_list ethernet physical wireless 
configuration: broadcast=yes driver=ipw2200 driverversion=1.2.2kmprq firmware=ABG:9.0.2.6 (Mar 22 2005) latency=32 maxlatency=24 mingnt=3 module=ipw2200 multicast=yes wireless=unassociated 
*-network:1 
description: Ethernet interface 
product: BCM4401-B0 100Base-TX 
vendor: Broadcom Corporation 
physical id: 5 
bus info: pci@0000:02:05.0 
logical name: eth1 
version: 02 
serial: 00:12:3f:82:70:d1 
width: 32 bits 
clock: 33MHz 
capabilities: bus_master cap_list ethernet physical 
configuration: broadcast=yes driver=b44 driverversion=2.0 latency=32 module=ssb multicast=yes 
fauzia@Fauzia:~$ iwlist scan 
lo Interface doesn't support scanning. 
 
eth1 Interface doesn't support scanning. 
 
eth0 Scan completed : 
Cell 01 - Address: 00:18:01:F4:4D:07 
ESSID:"TRUO3" 
Protocol:IEEE 802.11bg 
Mode:Master 
Frequency:2.412 GHz (Channel 1) 
Encryption key:on 
Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s 
11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s 
48 Mb/s; 54 Mb/s 
Quality=86/100 Signal level=-44 dBm 
Extra: Last beacon: 4ms ago 
Cell 02 - Address: 00:14:BF:AD:BD:C1 
ESSID:"RADHOME" 
Protocol:IEEE 802.11bg 
Mode:Master 
Frequency:2.437 GHz (Channel 6) 
Encryption key:on 
Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s 
11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s 
48 Mb/s; 54 Mb/s 
Quality=55/100 Signal level=-68 dBm 
IE: WPA Version 1 
Group Cipher : TKIP 
Pairwise Ciphers (1) : TKIP 
Authentication Suites (1) : PSK 
Extra: Last beacon: 224ms ago 
Cell 03 - Address: 00:18:01:FD:18:3A 
ESSID:"PlusNet" 
Protocol:IEEE 802.11bg 
Mode:Master 
Frequency:2.437 GHz (Channel 6) 
Encryption key:on 
Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s 
11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s 
48 Mb/s; 54 Mb/s 
Quality=33/100 Signal level=-80 dBm 
IE: WPA Version 1 
Group Cipher : CCMP 
Pairwise Ciphers (1) : CCMP 
Authentication Suites (1) : PSK 
IE: IEEE 802.11i/WPA2 Version 1 
Group Cipher : CCMP 
Pairwise Ciphers (1) : CCMP 
Authentication Suites (1) : PSK 
Extra: Last beacon: 612ms ago 
Cell 04 - Address: 00:0F:B5:E8:45:84 
ESSID:"DEONET" 
Protocol:IEEE 802.11bg 
Mode:Master 
Frequency:2.452 GHz (Channel 9) 
Encryption key:on 
Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 9 Mb/s; 11 Mb/s 
6 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s 
48 Mb/s; 54 Mb/s 
Quality=27/100 Signal level=-83 dBm 
Extra: Last beacon: 540ms ago 
Cell 05 - Address: 00:0F:B5:1A:44:8C 
ESSID:"AlwaysConnected" 
Protocol:IEEE 802.11bg 
Mode:Master 
Frequency:2.457 GHz (Channel 10) 
Encryption key:off 
Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s 
11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s 
48 Mb/s; 54 Mb/s 
Quality=86/100 Signal level=-72 dBm 
Extra: Last beacon: 76ms ago 
Cell 06 - Address: 00:18:01:E8:8C:40 
ESSID:"SirMaddog" 
Protocol:IEEE 802.11bg 
Mode:Master 
Frequency:2.422 GHz (Channel 3) 
Encryption key:on 
Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s 
11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s 
48 Mb/s; 54 Mb/s 
Quality=29/100 Signal level=-82 dBm 
Extra: Last beacon: 676ms ago 
 
fauzia@Fauzia:~$ sudo iwconfig essid ¨TRU03¨ mode managed 
iwconfig: unknown command "¨TRU03¨" 
fauzia@Fauzia:~$ sudo dhclient eth0 
Internet Systems Consortium DHCP Client V3.0.6 
Copyright 2004-2007 Internet Systems Consortium. 
All rights reserved. 
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/) 
 
Listening on LPF/eth0/00:13:ce:37:5b:9e 
Sending on LPF/eth0/00:13:ce:37:5b:9e 
Sending on Socket/fallback 
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3 
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8 
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7 
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 11 
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 13 
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 19 
No DHCPOFFERS received.

```
 
 
Thank you once again for helping me.
 
-Fauzia

---

### Post by pytheas22 on 2008-10-01
Are you sure you get an IP address when you connect?  In the output that you posted above, you didn't have any IP addresses assigned, and you weren't actually associated with the wireless router.  But everything else appears to look alright...

You may want to try connecting using [wicd]("http://wicd.sourceforge.net") instead of Network Manager; many people have better luck with wicd (note that you will need to uninstall NM in order to install wicd; if for some reason you want NM back at a later date, type 'sudo apt-get install network-manager-gnome').  It may also help to disable all security on your wireless network and try connecting again.

Please let me know if any of that helps; otherwise we can look further into the problem.

---

### Post by iponeverything on 2008-10-01
Lets see if we can get any useful information from syslog.. try

grep NetworkManager: /var/log/syslog

and post back with about the last 100 lines or so.

---

### Post by flala on 2008-10-01
Pytheas:
I ran into a rather troublesome problem. I thought I'd be able to uninstall network manager through Applications->Add/Remove. But after doing that when I tried to install wicd, I got an error saying that Network Manager is installed and conflicting. So I believe using Add/Remove I only managed to disabled NM.

Then I ran this to uninstall NM:
```
sudo apt-get remove NetworkManager
```
but no luck. I got an error saying that NM was not found. I tried to go back and enable it so that I can uninstall it maybe? But I need a "working internet connection" to do that. So strange. I ran into a circular problem. Now I don't know what to do :( Any ideas?

iponeverything:
Sorry, I tried your after I tried pytheas' method i.e. after I disabled Network Manager. Here's the result. IT most certainly is fewer than a 100 lines and it's ALL that I got.

```
fauzia@Fauzia:~$ grep NetworkManager: /var/log/syslog 
Oct  1 10:27:24 Fauzia NetworkManager: <debug> [1222882044.573024] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_457_151_2dc4b147ed0472_if0_scsi_host_scsi_device_lun0_scsi_generic').  
Oct  1 10:27:25 Fauzia NetworkManager: <debug> [1222882045.048292] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/volume_uuid_3C3F_B35B').  
Oct  1 10:27:25 Fauzia NetworkManager: <debug> [1222882045.060142] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/storage_serial_USB_2_0_Flash_Disk_2dc4b147ed0472_0_0').  
Oct  1 10:27:25 Fauzia NetworkManager: <debug> [1222882045.064350] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_457_151_2dc4b147ed0472_if0_scsi_host_scsi_device_lun0').  
Oct  1 10:27:25 Fauzia NetworkManager: <debug> [1222882045.067413] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_457_151_2dc4b147ed0472_if0_scsi_host').  
Oct  1 10:27:25 Fauzia NetworkManager: <debug> [1222882045.075596] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_457_151_2dc4b147ed0472_if0').  
Oct  1 10:27:25 Fauzia NetworkManager: <debug> [1222882045.077246] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_457_151_2dc4b147ed0472').  
Oct  1 10:47:00 Fauzia NetworkManager: <info>  starting...  
Oct  1 10:47:08 Fauzia NetworkManager: <info>  Found radio killswitch /org/freedesktop/Hal/devices/dell_wlan_switch  
Oct  1 10:47:08 Fauzia NetworkManager: <info>  eth1: Device is fully-supported using driver '(null)'.  
Oct  1 10:47:08 Fauzia NetworkManager: <info>  nm_device_init(): waiting for device's worker thread to start  
Oct  1 10:47:08 Fauzia NetworkManager: <info>  nm_device_init(): device's worker thread started, continuing.  
Oct  1 10:47:08 Fauzia NetworkManager: <info>  Now managing wired Ethernet (802.3) device 'eth1'.  
Oct  1 10:47:08 Fauzia NetworkManager: <info>  Deactivating device eth1.  
Oct  1 10:47:08 Fauzia NetworkManager: <info>  Error getting killswitch power: org.freedesktop.Hal.Device.KillSwitch.NotSupported - Access type not supported  
Oct  1 10:47:08 Fauzia NetworkManager: <info>  Wireless now enabled by radio killswitch  
Oct  1 10:47:08 Fauzia NetworkManager: <debug> [1222883228.581858] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_bluetooth').  
Oct  1 10:47:12 Fauzia NetworkManager: <debug> [1222883232.127771] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_3582_drm_i915_card0').  
Oct  1 10:47:12 Fauzia NetworkManager: <debug> [1222883232.133345] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_8086_3582_0_drm_i915_card1').  
fauzia@Fauzia:~$ 
``` 

Does that give any leads? Thank you so much for helping me.

---

### Post by pytheas22 on 2008-10-01
The package manager should have automatically known to uninstall NM when wicd was installed, but maybe for some reason it didn't.  Either way, you can uninstall Network Manager yourself by typing:
```

sudo apt-get remove network-manager
```

And you should be able to install wicd, even without an Internet connection, by downloading [this package]("http://downloads.sourceforge.net/wicd/wicd_1.5.3_all.deb?modtime=1222631284&big_mirror=0"), transferring it to your Ubuntu machine, and double-clicking on it to install it.  I don't think that it has any dependencies, so it should just install.  If not, let me know.

Please let us know if wicd makes a difference.

Also, to disable encryption, you generally would open up a web browser, and put '192.168.1.1' or '192.168.0.1' in the address bar (if it asks you for a username and password, they're usually printed on the outside of your router somewhere, or if not, let us know the router model and we can probably look up the default credentials).  It should bring you to a configuration page for your router, where you can disable wireless security.  Can you connect with wireless security disabled?

There also seems to be an unsecured network in your neighborhood named 'AlwaysConnected' that gives good signal strength.  If you can connect to that network in Windows, try connecting to it in Ubuntu as well (I say to try Windows first because the network may be secured another way even though it has no encryption key, so try connecting in Windows just to see if it really lets anyone connect).

---

### Post by flala on 2008-10-07
I am so sorry for the late reply. The good news though, after all this effort, is that my internet connection works! :)

Here are some details I should tell you:
1) sudo apt-get remove network-manager worked. The command I was using earlier apparently was incorrect.
2) Thus, I could also install wicd.
3) Could not connect to AlwaysConnected. After trying wicd would read ¨not connected.¨
4) I could not disable encryption either. My internet browser would display an error message reading ¨failed to connect.¨

Here&#347; what worked though:
1) In the wicd window (Applications->Internet->wicd network) my connection was displayed on top. I clicked on the triangle on its left.
2) Then I opened ¨Advance Settings¨ and chose ¨WEP (Hex)¨ and under ¨Key¨ I enter my WEP key. 
3) I clicked on the triangle again and hit connect. It connected right away. 

I am logged into ubuntu right now and sending you this message. So excited! Thank you so much for helping. I couldn´t have done this without your help.

-Fauzia

---

### Post by pytheas22 on 2008-10-07
Glad to hear that it worked.  I guess Network Manager was the problem all along.

Enjoy Ubuntu :)

---

### Post by flala on 2008-10-08
That's what it seems like. Thank you!

---

