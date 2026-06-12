---
title: "Wireless NIC Card Problem on Toshiba Satellite"
date: 2005-07-08
forum: Hardware &amp; Laptops
---

### Post by phreaky on 2005-07-08
I currently have a Toshiba Satellite Laptop. I installed Ubuntu yesterday. Everything seems to work ok except my touch pad and my wireless card. I found a fix for the touch pad so that should be ok. My wireless card on the other hand doesn't seem to be working properly. It is configured/active and it says it is connnected and it has a signal. I can not ping my router nor anything else. Normally I connect to it via DHCP but it doesn't seem to work at all that way. When I configure it and give myself a static ip on my router thats when it says its connected but I can't ping anything. When I click the drop down menu with the different wireless networks it has mine and the others near me listed so it seems to be working. I just can't ping anything or load any webpages. Any ideas on something else I can try?

---

### Post by magoo on 2005-07-08
Hello

please give us more details, when it should be configured.

output

```

# card type
$ lspci
or
$ lspci | grep -i ethernet

# wireless config
$ sudo iwconfig

# network config
$ sudo ifconfig

# routing config
$ netstat -rn

# dhcp is running ?
$ ps aux | grep dhc

$ cat /etc/network/interfaces

```

wireless configuration type (WEP or not, WPA...) no need to give keys...

What have you done to configure it?

Does this show your access point (ESSID)?
```

$ iwlist scan

```

Has the wireless-tools been installed (I don't know if this is by default or not) ?

---

### Post by phreaky on 2005-07-10
Sorry for the delay in posting. I attempted to fix my touchpad mouse and it ended up breaking the whole system. I had to reinstall everything. Here is the outputs for everythign you requested.

root@raven:/home/michael # lspci | grep -i ethernet
0000:02:02.0 Ethernet controller: Atheros Communications, Inc. AR5212 802.11abg NIC (rev 01)
0000:02:03.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
root@raven:/home/michael #

root@raven:/home/michael # sudo iwconfig
lo        no wireless extensions.

ath0      IEEE 802.11  ESSID:"EnforcedNET"
          Mode:Managed  Frequency:2.442 GHz  Access Point: FF:FF:FF:FF:FF:FF
          Bit Rate:1 Mb/s   Tx-Power:50 dBm   Sensitivity=0/3
          Retry:off   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality=37/94  Signal level=-58 dBm  Noise level=-95 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

eth0      no wireless extensions.

sit0      no wireless extensions.

root@raven:/home/michael #

root@raven:/home/michael # sudo ifconfig
ath0      Link encap:Ethernet  HWaddr 00:11:F5:03:78:9F
          inet6 addr: fe80::211:f5ff:fe03:789f/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:855 dropped:0 overruns:0 frame:855
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:199
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:18 Memory:dcae0000-dcaf0000

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:8344 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8344 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:528276 (515.8 KiB)  TX bytes:528276 (515.8 KiB)

root@raven:/home/michael #

root@raven:/home/michael # netstat -rn
Kernel IP routing table
Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface
root@raven:/home/michael #

root@raven:/home/michael # ps aux | grep dhc
root     10089  0.0  0.2   2136   960 ?        Ss   11:55   0:00 /sbin/dhclient3 -pf /var/run/dhclient.ath0.pid ath0
root     12085  0.0  0.1   3032   716 pts/0    S+   11:59   0:00 grep dhc
root@raven:/home/michael #

root@raven:/home/michael # cat /etc/network/interfaces
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
mapping hotplug
        script grep
        map ath0

iface ath0 inet dhcp
wireless-essid EnforcedNET
wireless-key PASSWORD WAS HERE

auto ath0
root@raven:/home/michael #

root@raven:/home/michael # iwlist scan
lo        Interface doesn't support scanning.

ath0      Scan completed :
          Cell 01 - Address: 00:0C:41:53:E5:1B
                    ESSID:"Jaronda"
                    Mode:Master
                    Frequency:2.462 GHz (Channel 11)
                    Quality=0/94  Signal level=-95 dBm  Noise level=-95 dBm
                    Encryption key:off
                    Bit Rate:1 Mb/s
                    Bit Rate:2 Mb/s
                    Bit Rate:5 Mb/s
                    Bit Rate:6 Mb/s
                    Bit Rate:9 Mb/s
                    Bit Rate:11 Mb/s
                    Bit Rate:12 Mb/s
                    Bit Rate:18 Mb/s
                    Bit Rate:24 Mb/s
                    Bit Rate:36 Mb/s
                    Bit Rate:48 Mb/s
                    Bit Rate:54 Mb/s
                    Extra:bcn_int=100
          Cell 02 - Address: 00:01:24:F2:BB:70
                    ESSID:"BodenheimInGermany"
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Quality=0/94  Signal level=-95 dBm  Noise level=-95 dBm
                    Encryption key:on
                    Bit Rate:1 Mb/s
                    Bit Rate:2 Mb/s
                    Bit Rate:5 Mb/s
                    Bit Rate:11 Mb/s
                    Extra:bcn_int=100
          Cell 03 - Address: 00:0C:41:8A:2A:6E
                    ESSID:"jtnet"
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Quality=0/94  Signal level=-95 dBm  Noise level=-95 dBm
                    Encryption key:on
                    Bit Rate:1 Mb/s
                    Bit Rate:2 Mb/s
                    Bit Rate:5 Mb/s
                    Bit Rate:11 Mb/s
                    Extra:bcn_int=100
          Cell 04 - Address: 00:09:5B:ED:AA:70
                    ESSID:"EnforcedNET"
                    Mode:Master
                    Frequency:2.417 GHz (Channel 2)
                    Quality=0/94  Signal level=-95 dBm  Noise level=-95 dBm
                    Encryption key:on
                    Bit Rate:1 Mb/s
                    Bit Rate:2 Mb/s
                    Bit Rate:5 Mb/s
                    Bit Rate:6 Mb/s
                    Bit Rate:9 Mb/s
                    Bit Rate:11 Mb/s
                    Bit Rate:12 Mb/s
                    Bit Rate:18 Mb/s
                    Bit Rate:24 Mb/s
                    Bit Rate:36 Mb/s
                    Bit Rate:48 Mb/s
                    Bit Rate:54 Mb/s
                    Extra:bcn_int=100
                    Extra:wpa_ie=dd160050f20101000050f20201000050f20201000050f202

eth0      Interface doesn't support scanning.

sit0      Interface doesn't support scanning.

root@raven:/home/michael #

The network is a WPA and I have tried to configure it though the System > Administration > Network. I put in the Key and then hit apply. Then hit ok. Then I set the ath0 as the defualt device and it just doesnt seem to configure.

---

### Post by magoo on 2005-07-11
> 
root@raven:/home/michael # lspci | grep -i ethernet
0000:02:02.0 Ethernet controller: Atheros Communications, Inc. AR5212 802.11abg NIC (rev 01)

madwifi driver

> 
root@raven:/home/michael # sudo iwconfig
ath0      IEEE 802.11  ESSID:"EnforcedNET"
          Mode:Managed  Frequency:2.442 GHz  Access Point: FF:FF:FF:FF:FF:FF

It is not associated with the access point

> 
root@raven:/home/michael # cat /etc/network/interfaces
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
mapping hotplug
        script grep
        map ath0

iface ath0 inet dhcp
wireless-essid EnforcedNET
wireless-key PASSWORD WAS HERE

auto ath0

This is the settings for static WEP key sites

> 
root@raven:/home/michael # iwlist scan
lo        Interface doesn't support scanning.

ath0      Scan completed :
          Cell 01 - Address: 00:0C:41:53:E5:1B
                    ESSID:"Jaronda"
                    Mode:Master
                    Frequency:2.462 GHz (Channel 11)
(...)
          Cell 02 - Address: 00:01:24:F2:BB:70
                    ESSID:"BodenheimInGermany"
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
(...)
          Cell 03 - Address: 00:0C:41:8A:2A:6E
                    ESSID:"jtnet"
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
(...)
          Cell 04 - Address: 00:09:5B:ED:AA:70
                    ESSID:"EnforcedNET"
                    Mode:Master
                    Frequency:2.417 GHz (Channel 2)
(...)
                Extra:wpa_ie=dd160050f20101000050f20201000050f20201000050f202

WPA site, if your wlan access point is only configured for WPA (and not static WEP at the same time), your setup will not work.

> 
The network is a WPA and I have tried to configure it though the System > Administration > Network. I put in the Key and then hit apply. Then hit ok. Then I set the ath0 as the defualt device and it just doesnt seem to configure.


Please see this post I made concerning WPA-PSK and wireless lan. (hint: <your_supported_wlan_card_type> is madwifi)
[http://www.ubuntuforums.org/showthread.php?t=47406](http://www.ubuntuforums.org/showthread.php?t=47406)

---

### Post by phreaky on 2005-07-16
I am still having problems. I checked the other post and tried to do that and its still not working.... any ideas or anything I can do to check to see if your post worked.

---

### Post by magoo on 2005-07-17
hello,
make sure wpa daemon is running:
```

magnus@bougie:~$ ps aux |grep wpa
root      5402  0.0  0.3   3120  1348 ?        S<s  09:12   0:00 wpa_supplicant -B -i ath0 -D madwifi
magnus@bougie:~$

```
then to check if wpa work is successfully interacting with your AP:
```

$ wpa_cli
> status
bssid=<bssid mac address here>
ssid=<your ssid here>
pairwise_cipher=TKIP
group_cipher=WEP-104
key_mgmt=WPA-PSK
wpa_state=COMPLETED
Supplicant PAE state=AUTHENTICATED
suppPortStatus=Authorized
EAP state=SUCCESS
>

```
then check if your wireless interface has a WEP key
```

magnus@bougie:~$ sudo iwconfig ath0
ath0      IEEE 802.11g  ESSID:"<your ssid here>"
          Mode:Managed  Frequency:2.437 GHz  Access Point: <AP mac address here>
          Bit Rate:54 Mb/s   Tx-Power:50 dBm   Sensitivity=0/3
          Retry:off   RTS thr:off   Fragment thr:off
          Encryption key:AE19-DE49-026C-55F6-58B2-C724-141F-E606   Security mode:restricted
          Power Management:off
          Link Quality=45/94  Signal level=-50 dBm  Noise level=-95 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:1

magnus@bougie:~$

```
This means that the encryption is up and running.
Then check if you got an IP address:
```

magnus@bougie:~$ sudo ifconfig ath0
ath0      Link encap:Ethernet  HWaddr 00:30:4F:37:B3:8E
          inet addr:10.7.8.128  Bcast:10.7.8.255  Mask:255.255.255.0
          inet6 addr: fe80::230:4fff:fe37:b38e/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:41215 errors:9 dropped:0 overruns:0 frame:9
          TX packets:36762 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:199
          RX bytes:42382782 (40.4 MiB)  TX bytes:4344805 (4.1 MiB)
          Interrupt:18 Memory:d8ba0000-d8bb0000

magnus@bougie:~$

```
If you arrive at this point, wpa and wireless is not the issue.

btw: what does not work? how do you test to say it does not work?

---

