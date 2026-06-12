---
title: "intel 3945abg can't connect."
date: 2008-05-13
forum: Hardware
---

### Post by marios_geo on 2008-05-13
Hi. I have a HP Pavilion 6680. This laptop has the intel 3945ABG wifi card.
I am using kubuntu 8.04. Kubuntu detects the card, finds the wireless network (signal, essid etc) but can't connect.
I am using wep encryption, and no authntication (open) (at least this is how i connect with windows).

There is a very similar problem like this
[https://bugs.launchpad.net/ubuntu/+s...er/+bug/121439](https://bugs.launchpad.net/ubuntu/+s...er/+bug/121439)
but kubuntu loads the iwl3945 driver.
The process stops when knetwotkmanager starts the ip configuration. But no error appears, just could not conect.

marios@artemis:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11g  ESSID:"SEISMOLOGICAL-AP"  Nickname:""
          Mode:Managed  Frequency:2.422 GHz  Access Point: 00:1A:70:47:32:87
          Bit Rate=48 Mb/s   Tx-Power=27 dBm
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B
          Power Management:off
          Link Quality=75/100  Signal level=-59 dBm  Noise level=-127 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0










marios@artemis:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:1b:24:f2:7a:17
          inet addr:155.207.124.13  Bcast:155.207.124.255  Mask:255.255.255.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:251 Base address:0x8000

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:12 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:1056 (1.0 KB)  TX bytes:1056 (1.0 KB)

wlan0     Link encap:Ethernet  HWaddr 00:1c:bf:85:37:e4
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:15 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 B)  TX bytes:2316 (2.2 KB)

wmaster0  Link encap:UNSPEC  HWaddr 00-1C-BF-85-37-E4-00-00-00-00-00-00-00-00-00-00
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)







marios@artemis:~$ lspci | grep 3945
02:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)




marios@artemis:~$ lsmod | grep 3945
iwl3945               100468  0
iwlwifi_mac80211      251876  1 iwl3945

---

### Post by hermes0710 on 2008-05-13
Is kde the only installed desktop you have? If not try logging in to Gnome and establishing the connection from that env. If it succeeds, check your knetworkmanager settings

---

### Post by marios_geo on 2008-05-14
I tried Mandriva 2008.1, and it seems to connect. I mean i get an ip adress and gateway via dhcp, but i can't ping anything outside the 192.168.1.X, so no dns either. Anyway i couldn't search it more, cause i got out of battery.
1) It's a big step since my last attempt with kubuntu
2) I don't want to change kubuntu.
Any ideas?

---

### Post by hermes0710 on 2008-05-14
I don't suggest change Kubuntu, just when you are in the login screen change session to gnome instead of kde

---

### Post by marios_geo on 2008-05-14
I am also a kde guy!!!. 
Which packet i need just to get the gnome-network manager

---

### Post by Zorael on 2008-05-14
```
wlan0 IEEE 802.11g ESSID:"SEISMOLOGICAL-AP" Nickname:""
Mode:Managed Frequency:2.422 GHz **Access Point: 00:1A:70:47:32:87**
Bit Rate=48 Mb/s Tx-Power=27 dBm
Retry min limit:7 RTS thrff Fragment thr=2346 B
Power Managementff
Link Quality=75/100 Signal level=-59 dBm Noise level=-127 dBm
Rx invalid nwid:0 Rx invalid crypt:0 Rx invalid frag:0
Tx excessive retries:0 Invalid misc:0 Missed beacon:0
```
That looks about right though, doesn't it? You're connected to the router. If you at this point can ping it but you can't access the outside internet then you likely just need to define the default route.
```
$ sudo route add -net default gw 192.168.1.1 dev wlan0
```
If that doesn't work right away, please post the output of just entering [FONT="Courier New"]route[/FONT] in a terminal.


To be harsh, KNetworkManager (and NetworkManager in general) isn't always at the top of the game - in my experience especially when it comes to managing routes. I only use the terminal commands, but you could give wicd a shot if you want a gui solution.

[http://wicd.sourceforge.net/](http://wicd.sourceforge.net/)

---

