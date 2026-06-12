---
title: "ubuntu 12.04 and wireless connection"
date: 2012-04-27
forum: Hardware
---

### Post by hossub on 2012-04-27
hi
i have install ubuntu 12.04 in my lenevo T40 , now i can only connect to my wireless but i cant ping or use internet,where is my problem?

i think ubuntu have some bug, because in ubuntu 11.10 my wireless wotk fine,i dont need configure my wireless.

note my wireless adapter is : Intel Centrino Advanced-N 6205 wireless card

---

### Post by zdeuyo on 2012-04-27
> **hossub said:**
> hi
i have install ubuntu 12.02 in my lenevo T40 , now i can only connect to my wireless but i can ping or use internet,where is my problem?

i think ubuntu have some bug, because in ubuntu 11.10 my wireless wotk fine,i dopnt need configure my wireless.

note my wireless adapter is : Intel Centrino Advanced-N 6205 wireless card

Hello,

Please try running the following code,

```

sudo apt-get update
sudo apt-get upgrade

```

Then restart.

If this does not work please try using this thread as a reference.

Link: [http://ubuntuforums.org/showthread.php?t=1959458]("http://ubuntuforums.org/showthread.php?t=1959458")

Please let me know if either of these fix your problem.

All the best.

---

### Post by hossub on 2012-04-27
thank you, but i am run this command:

```
dmesg | grep iwl
rfkill list all

```
this is result:
```
[   18.893038] iwlwifi 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   18.893070] iwlwifi 0000:03:00.0: setting latency timer to 64
[   18.893107] iwlwifi 0000:03:00.0: pci_resource_len = 0x00002000
[   18.893108] iwlwifi 0000:03:00.0: pci_resource_base = f8458000
[   18.893110] iwlwifi 0000:03:00.0: HW Revision ID = 0x34
[   18.893242] iwlwifi 0000:03:00.0: irq 44 for MSI/MSI-X
[   18.893317] iwlwifi 0000:03:00.0: Detected Intel(R) Centrino(R) Advanced-N 6205 AGN, REV=0xB0
[   18.893422] iwlwifi 0000:03:00.0: L1 Enabled; Disabling L0S
[   18.902398] iwlwifi 0000:03:00.0: device EEPROM VER=0x715, CALIB=0x6
[   18.902399] iwlwifi 0000:03:00.0: Device SKU: 0X1f0
[   18.902401] iwlwifi 0000:03:00.0: Valid Tx ant: 0X3, Valid Rx ant: 0X3
[   18.902422] iwlwifi 0000:03:00.0: Tunable channels: 13 802.11bg, 24 802.11a channels
[   19.226352] iwlwifi 0000:03:00.0: loaded firmware version 17.168.5.3 build 42301
[   19.629493] ieee80211 phy0: Selected rate control algorithm 'iwl-agn-rs'
[   25.325608] iwlwifi 0000:03:00.0: L1 Enabled; Disabling L0S
[   25.325783] iwlwifi 0000:03:00.0: Radio type=0x1-0x2-0x0
[   25.611526] iwlwifi 0000:03:00.0: L1 Enabled; Disabling L0S
[   25.611717] iwlwifi 0000:03:00.0: Radio type=0x1-0x2-0x0
[  104.726154] iwlwifi 0000:03:00.0: Tx aggregation enabled on ra = c8:6c:87:8c:44:dc tid = 0

```
and
```
0: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no
1: tpacpi_bluetooth_sw: Bluetooth
	Soft blocked: no
	Hard blocked: no
2: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no

```

now what i am must to do?

---

### Post by zdeuyo on 2012-04-27
> **hossub said:**
> thank you, but i am run this command:

```
dmesg | grep iwl
rfkill list all

```
this is result:
```
[   18.893038] iwlwifi 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   18.893070] iwlwifi 0000:03:00.0: setting latency timer to 64
[   18.893107] iwlwifi 0000:03:00.0: pci_resource_len = 0x00002000
[   18.893108] iwlwifi 0000:03:00.0: pci_resource_base = f8458000
[   18.893110] iwlwifi 0000:03:00.0: HW Revision ID = 0x34
[   18.893242] iwlwifi 0000:03:00.0: irq 44 for MSI/MSI-X
[   18.893317] iwlwifi 0000:03:00.0: Detected Intel(R) Centrino(R) Advanced-N 6205 AGN, REV=0xB0
[   18.893422] iwlwifi 0000:03:00.0: L1 Enabled; Disabling L0S
[   18.902398] iwlwifi 0000:03:00.0: device EEPROM VER=0x715, CALIB=0x6
[   18.902399] iwlwifi 0000:03:00.0: Device SKU: 0X1f0
[   18.902401] iwlwifi 0000:03:00.0: Valid Tx ant: 0X3, Valid Rx ant: 0X3
[   18.902422] iwlwifi 0000:03:00.0: Tunable channels: 13 802.11bg, 24 802.11a channels
[   19.226352] iwlwifi 0000:03:00.0: loaded firmware version 17.168.5.3 build 42301
[   19.629493] ieee80211 phy0: Selected rate control algorithm 'iwl-agn-rs'
[   25.325608] iwlwifi 0000:03:00.0: L1 Enabled; Disabling L0S
[   25.325783] iwlwifi 0000:03:00.0: Radio type=0x1-0x2-0x0
[   25.611526] iwlwifi 0000:03:00.0: L1 Enabled; Disabling L0S
[   25.611717] iwlwifi 0000:03:00.0: Radio type=0x1-0x2-0x0
[  104.726154] iwlwifi 0000:03:00.0: Tx aggregation enabled on ra = c8:6c:87:8c:44:dc tid = 0

```
and
```
0: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no
1: tpacpi_bluetooth_sw: Bluetooth
	Soft blocked: no
	Hard blocked: no
2: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no

```

now what i am must to do?

Hello,

I forwarded your issue to the person who helped me solve the previous thread. He is the person referenced in that thread link.

---

### Post by chili555 on 2012-04-27
Please show me:```
iwconfig
route -n
ifconfig
```Thanks.

---

### Post by austinap on 2012-04-27
Sorry to Hijak, but I'm having the same problem.

rfkil list all
```
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

```iwconfig
```
lo        no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:"athens"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:24:6C:AB:B2:20   
          Bit Rate=1 Mb/s   Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=53/70  Signal level=-57 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

eth0      no wireless extensions.

```route -n
```
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         156.111.130.1   0.0.0.0         UG    0      0        0 wlan0
156.111.130.0   0.0.0.0         255.255.254.0   U     2      0        0 wlan0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 wlan0
```ifconfig
```
eth0      Link encap:Ethernet  HWaddr f0:4d:a2:f4:c9:7d  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:44 Base address:0x8000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1211 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1211 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:140570 (140.5 KB)  TX bytes:140570 (140.5 KB)

wlan0     Link encap:Ethernet  HWaddr c0:f8:da:5f:14:89  
          inet addr:156.111.131.98  Bcast:156.111.131.255  Mask:255.255.254.0
          inet6 addr: fe80::c2f8:daff:fe5f:1489/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:359 errors:0 dropped:0 overruns:0 frame:0
          TX packets:129 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:69506 (69.5 KB)  TX bytes:17696 (17.6 KB)
```

I'll be forever indebted to anyone that can give me suggestions!

---

### Post by chili555 on 2012-04-27
> Sorry to Hijak, but I'm having the same problem.Now let's see:```
ping -c3 156.111.130.1
ping -c3 173.194.73.106
cat /etc/resolv.conf
```Thanks.

---

### Post by austinap on 2012-04-27
ping -c3 156.111.130.1
```
PING 156.111.130.1 (156.111.130.1) 56(84) bytes of data.
From 156.111.131.98 icmp_seq=1 Destination Port Unreachable
From 156.111.131.98 icmp_seq=2 Destination Port Unreachable
From 156.111.131.98 icmp_seq=3 Destination Port Unreachable

--- 156.111.130.1 ping statistics ---
3 packets transmitted, 0 received, +3 errors, 100% packet loss, time 1999ms
```


ping -c3 173.194.73.106
```
PING 173.194.73.106 (173.194.73.106) 56(84) bytes of data.
From 156.111.131.98 icmp_seq=1 Destination Port Unreachable
From 156.111.131.98 icmp_seq=2 Destination Port Unreachable
From 156.111.131.98 icmp_seq=3 Destination Port Unreachable

--- 173.194.73.106 ping statistics ---
3 packets transmitted, 0 received, +3 errors, 100% packet loss, time 1998ms
```

cat /etc/resolv.conf
```
# Dynamic resolv.conf(5) file for glibc resolver(3) generated by resolvconf(8)
#     DO NOT EDIT THIS FILE BY HAND -- YOUR CHANGES WILL BE OVERWRITTEN
nameserver 127.0.0.1
search cpmc.columbia.edu
```

---

### Post by chili555 on 2012-04-27
> cat /etc/resolv.conf
Code:

# Dynamic resolv.conf(5) file for glibc resolver(3) generated by resolvconf(8)
#     DO NOT EDIT THIS FILE BY HAND -- YOUR CHANGES WILL BE OVERWRITTEN
nameserver 127.0.0.1
search cpmc.columbia.edu

That's...err, interesting. You might consult with the IT gals/guys at Columbia to see what that all means. Let's overwrite the file after making a backup and see if things improve:```
sudo cp /etc/resolv.conf /etc/resolv.bak
```Now let's put a known good nameserver in a new file:```
sudo gedit /etc/resolv.conf
```A new empty file will open; add:```
nameserver 8.8.8.8
```Proofread, save and close gedit. Now do:```
ping -c3 156.111.130.1
ping -c3 173.194.73.106
```Any change?

---

### Post by austinap on 2012-04-27
As soon as I reconnect my wireless, the changes are overwritten.  Any ideas?  I've been hesitant to call IT as I'm not sure how linux friendly they're going to be here, and things were working just fine under 11.10.

**Edit: and the're closed for the weekend...

---

### Post by chili555 on 2012-04-27
> **austinap said:**
> As soon as I reconnect my wireless, the changes are overwritten.  Any ideas?  I've been hesitant to call IT as I'm not sure how linux friendly they're going to be here, and things were working just fine under 11.10.

**Edit: and the're closed for the weekend...But when you made the change, did it work correctly? It's OK to leave the wireless connected while you make the change. Let's also look at:```
cat /etc/hosts
```

---

### Post by austinap on 2012-04-27
Sorry for being unclear.  The pings still didn't go through after editing /etc/resolv.conf.

As for /etc/hosts:
```

127.0.0.1       localhost
127.0.1.1       austin-Inspiron-620

# The following lines are desirable for IPv6 capable hosts
::1           ip6-localhost ip6-loopback
fe00::0     ip6-localnet
ff00::0     ip6-mcastprefix
ff02::1     ip6-allnodes
ff02::2     ip6-allrouters

```

Thanks again for all your help so far!

---

### Post by chili555 on 2012-04-27
I wonder if you are actually, really connected! Are you using Network Manager? May I assume it asserts it *is* connected? May I see:```
dmesg | grep wlan
sudo cat /var/log/syslog | grep etwork | tail -n20
```

---

### Post by austinap on 2012-04-27
Here's dmesg | grep wlan:
```
[ 7223.475400] wlan0: deauthenticating from 00:24:6c:ab:8f:a0 by local choice (reason=3)
[ 7226.902102] wlan0: authenticate with 00:24:6c:ab:b2:50 (try 1)
[ 7226.904035] wlan0: authenticated
[ 7226.922674] wlan0: associate with 00:24:6c:ab:b2:50 (try 1)
[ 7226.927310] wlan0: RX ReassocResp from 00:24:6c:ab:b2:50 (capab=0x431 status=0 aid=1)
[ 7226.927314] wlan0: associated
[ 7238.682476] wlan0: no IPv6 routers present
[ 7263.535005] wlan0: authenticate with 00:24:6c:ab:8f:a0 (try 1)
[ 7263.548832] wlan0: authenticated
[ 7263.590804] wlan0: associate with 00:24:6c:ab:8f:a0 (try 1)
[ 7263.595047] wlan0: RX ReassocResp from 00:24:6c:ab:8f:a0 (capab=0x431 status=0 aid=3)
[ 7263.595052] wlan0: associated
[ 7263.595111] wlan0: Wrong control channel in association response: configured center-freq: 2412 hti-cfreq: 2462  hti->control_chan: 11 band: 0.  Disabling HT.
[ 7489.147013] wlan0: deauthenticating from 00:24:6c:ab:8f:a0 by local choice (reason=3)
[ 7492.229485] wlan0: authenticate with 00:24:6c:ab:8f:a0 (try 1)
[ 7492.233182] wlan0: authenticated
[ 7492.251859] wlan0: associate with 00:24:6c:ab:8f:a0 (try 1)
[ 7492.255997] wlan0: RX ReassocResp from 00:24:6c:ab:8f:a0 (capab=0x431 status=0 aid=2)
[ 7492.256002] wlan0: associated
[ 7492.256058] wlan0: Wrong control channel in association response: configured center-freq: 2412 hti-cfreq: 2462  hti->control_chan: 11 band: 0.  Disabling HT.
[ 7503.068233] wlan0: no IPv6 routers present
[ 7542.005443] wlan0: authenticate with 00:24:6c:ab:b3:10 (try 1)
[ 7542.007381] wlan0: authenticated
[ 7542.089125] wlan0: associate with 00:24:6c:ab:b3:10 (try 1)
[ 7542.097454] wlan0: RX ReassocResp from 00:24:6c:ab:b3:10 (capab=0x431 status=0 aid=1)
[ 7542.097458] wlan0: associated
[ 7552.080139] wlan0: disassociating from 00:24:6c:ab:b3:10 by local choice (reason=3)
[ 7552.110775] wlan0: deauthenticating from 00:24:6c:ab:b3:10 by local choice (reason=3)
[ 7553.149341] wlan0: authenticate with 00:24:6c:ab:b3:10 (try 1)
[ 7553.152079] wlan0: authenticated
[ 7553.170816] wlan0: associate with 00:24:6c:ab:b3:10 (try 1)
[ 7553.188816] wlan0: RX ReassocResp from 00:24:6c:ab:b3:10 (capab=0x431 status=0 aid=1)
[ 7553.188821] wlan0: associated
[ 7610.608364] wlan0: direct probe to 00:24:6c:ab:8f:a0 (try 1/3)
[ 7610.617234] wlan0: direct probe responded
[ 7610.617313] wlan0: authenticate with 00:24:6c:ab:8f:a0 (try 1)
[ 7610.623893] wlan0: authenticated
[ 7610.729835] wlan0: associate with 00:24:6c:ab:8f:a0 (try 1)
[ 7610.734079] wlan0: RX ReassocResp from 00:24:6c:ab:8f:a0 (capab=0x431 status=0 aid=2)
[ 7610.734084] wlan0: associated
[ 7610.734145] wlan0: Wrong control channel in association response: configured center-freq: 2412 hti-cfreq: 2462  hti->control_chan: 11 band: 0.  Disabling HT.
[ 7612.139365] wlan0: authenticate with 00:24:6c:ab:b2:50 (try 1)
[ 7612.148300] wlan0: authenticated
[ 7612.180460] wlan0: associate with 00:24:6c:ab:b2:50 (try 1)
[ 7612.184826] wlan0: RX ReassocResp from 00:24:6c:ab:b2:50 (capab=0x431 status=0 aid=1)
[ 7612.184831] wlan0: associated
[ 7643.081337] wlan0: authenticate with 00:24:6c:ab:8f:a0 (try 1)
[ 7643.085843] wlan0: authenticated
[ 7643.137072] wlan0: associate with 00:24:6c:ab:8f:a0 (try 1)
[ 7643.141298] wlan0: RX ReassocResp from 00:24:6c:ab:8f:a0 (capab=0x431 status=0 aid=2)
[ 7643.141302] wlan0: associated
[ 7643.141366] wlan0: Wrong control channel in association response: configured center-freq: 2412 hti-cfreq: 2462  hti->control_chan: 11 band: 0.  Disabling HT.
[ 7925.270016] wlan0: deauthenticating from 00:24:6c:ab:8f:a0 by local choice (reason=3)
[ 7928.167058] wlan0: authenticate with 00:24:6c:ab:8f:a0 (try 1)
[ 7928.171275] wlan0: authenticated
[ 7928.190029] wlan0: associate with 00:24:6c:ab:8f:a0 (try 1)
[ 7928.194213] wlan0: RX ReassocResp from 00:24:6c:ab:8f:a0 (capab=0x431 status=0 aid=2)
[ 7928.194217] wlan0: associated
[ 7928.194279] wlan0: Wrong control channel in association response: configured center-freq: 2412 hti-cfreq: 2462  hti->control_chan: 11 band: 0.  Disabling HT.
[ 7938.295679] wlan0: no IPv6 routers present
[ 8000.660140] wlan0: direct probe to 00:24:6c:ab:b2:50 (try 1/3)
[ 8000.664874] wlan0: direct probe responded
[ 8000.723556] wlan0: authenticate with 00:24:6c:ab:b2:50 (try 1)
[ 8000.725459] wlan0: authenticated
[ 8000.789803] wlan0: associate with 00:24:6c:ab:b2:50 (try 1)
[ 8000.795066] wlan0: RX ReassocResp from 00:24:6c:ab:b2:50 (capab=0x431 status=0 aid=1)
[ 8000.795070] wlan0: associated
[ 8040.522013] wlan0: authenticate with 00:24:6c:ab:8f:a0 (try 1)
[ 8040.526757] wlan0: authenticated
[ 8040.653200] wlan0: associate with 00:24:6c:ab:8f:a0 (try 1)
[ 8040.657367] wlan0: RX ReassocResp from 00:24:6c:ab:8f:a0 (capab=0x431 status=0 aid=2)
[ 8040.657372] wlan0: associated
[ 8040.657432] wlan0: Wrong control channel in association response: configured center-freq: 2412 hti-cfreq: 2462  hti->control_chan: 11 band: 0.  Disabling HT.
[ 8488.360882] wlan0: direct probe to 00:24:6c:ab:b2:50 (try 1/3)
[ 8488.560090] wlan0: direct probe to 00:24:6c:ab:b2:50 (try 2/3)
[ 8488.759565] wlan0: direct probe to 00:24:6c:ab:b2:50 (try 3/3)
[ 8488.763574] wlan0: direct probe responded
[ 8488.767608] wlan0: authenticate with 00:24:6c:ab:b2:50 (try 1)
[ 8488.769531] wlan0: authenticated
[ 8488.839598] wlan0: associate with 00:24:6c:ab:b2:50 (try 1)
[ 8488.847430] wlan0: RX ReassocResp from 00:24:6c:ab:b2:50 (capab=0x431 status=0 aid=1)
[ 8488.847435] wlan0: associated
[ 8490.240040] wlan0: authenticate with 00:24:6c:ab:8f:a0 (try 1)
[ 8490.247516] wlan0: authenticated
[ 8490.311816] wlan0: associate with 00:24:6c:ab:8f:a0 (try 1)
[ 8490.316052] wlan0: RX ReassocResp from 00:24:6c:ab:8f:a0 (capab=0x431 status=0 aid=2)
[ 8490.316057] wlan0: associated
[ 8490.316117] wlan0: Wrong control channel in association response: configured center-freq: 2412 hti-cfreq: 2462  hti->control_chan: 11 band: 0.  Disabling HT.
[ 8552.113333] wlan0: authenticate with 00:24:6c:ab:b2:50 (try 1)
[ 8552.115986] wlan0: authenticated
[ 8552.161106] wlan0: associate with 00:24:6c:ab:b2:50 (try 1)
[ 8552.165408] wlan0: RX ReassocResp from 00:24:6c:ab:b2:50 (capab=0x431 status=0 aid=1)
[ 8552.165413] wlan0: associated
[ 8583.049954] wlan0: authenticate with 00:24:6c:ab:8f:a0 (try 1)
[ 8583.054890] wlan0: authenticated
[ 8583.149578] wlan0: associate with 00:24:6c:ab:8f:a0 (try 1)
[ 8583.157377] wlan0: RX ReassocResp from 00:24:6c:ab:8f:a0 (capab=0x431 status=0 aid=2)
[ 8583.157382] wlan0: associated
[ 8583.157446] wlan0: Wrong control channel in association response: configured center-freq: 2412 hti-cfreq: 2462  hti->control_chan: 11 band: 0.  Disabling HT.

```

And here's the tail of syslog:
```
Apr 27 18:49:30 austin-Inspiron-620 NetworkManager[943]: <info> (wlan0): roamed from BSSID 00:24:6C:AB:8F:A0 (athens) to 00:24:6C:AB:B2:50 (athens)
Apr 27 18:50:08 austin-Inspiron-620 NetworkManager[943]: <info> (wlan0): supplicant interface state: completed -> authenticating
Apr 27 18:50:08 austin-Inspiron-620 NetworkManager[943]: <info> (wlan0): supplicant interface state: authenticating -> associating
Apr 27 18:50:08 austin-Inspiron-620 NetworkManager[943]: <info> (wlan0): supplicant interface state: associating -> 4-way handshake
Apr 27 18:50:08 austin-Inspiron-620 NetworkManager[943]: <info> (wlan0): supplicant interface state: 4-way handshake -> completed
Apr 27 18:50:12 austin-Inspiron-620 NetworkManager[943]: <info> (wlan0): roamed from BSSID 00:24:6C:AB:B2:50 (athens) to 00:24:6C:AB:8F:A0 (athens)
Apr 27 18:57:37 austin-Inspiron-620 NetworkManager[943]: <info> (wlan0): supplicant interface state: completed -> authenticating
Apr 27 18:57:37 austin-Inspiron-620 NetworkManager[943]: <info> (wlan0): supplicant interface state: authenticating -> associating
Apr 27 18:57:37 austin-Inspiron-620 NetworkManager[943]: <info> (wlan0): supplicant interface state: associating -> completed
Apr 27 18:57:38 austin-Inspiron-620 NetworkManager[943]: <info> (wlan0): supplicant interface state: completed -> authenticating
Apr 27 18:57:39 austin-Inspiron-620 NetworkManager[943]: <info> (wlan0): supplicant interface state: authenticating -> associating
Apr 27 18:57:39 austin-Inspiron-620 NetworkManager[943]: <info> (wlan0): supplicant interface state: associating -> completed
Apr 27 18:58:41 austin-Inspiron-620 NetworkManager[943]: <info> (wlan0): supplicant interface state: completed -> authenticating
Apr 27 18:58:41 austin-Inspiron-620 NetworkManager[943]: <info> (wlan0): supplicant interface state: authenticating -> associating
Apr 27 18:58:41 austin-Inspiron-620 NetworkManager[943]: <info> (wlan0): supplicant interface state: associating -> completed
Apr 27 18:58:42 austin-Inspiron-620 NetworkManager[943]: <info> (wlan0): roamed from BSSID 00:24:6C:AB:8F:A0 (athens) to 00:24:6C:AB:B2:50 (athens)
Apr 27 18:59:12 austin-Inspiron-620 NetworkManager[943]: <info> (wlan0): supplicant interface state: completed -> authenticating
Apr 27 18:59:12 austin-Inspiron-620 NetworkManager[943]: <info> (wlan0): supplicant interface state: authenticating -> associating
Apr 27 18:59:12 austin-Inspiron-620 NetworkManager[943]: <info> (wlan0): supplicant interface state: associating -> completed
Apr 27 18:59:18 austin-Inspiron-620 NetworkManager[943]: <info> (wlan0): roamed from BSSID 00:24:6C:AB:B2:50 (athens) to 00:24:6C:AB:8F:A0 (athens)

```

---

### Post by austinap on 2012-04-28
Just wanted to update you on the problem.  Turns out it was all due to Mobloquer.  During the update, the block list got updated to include my school's domain, so it would let me connect to the internet, it just wouldn't let anything go over the connection.  Thanks again for all of your help!

---

### Post by hossub on 2012-04-28
> **chili555 said:**
> Please show me:```
iwconfig
route -n
ifconfig
```Thanks.

```
hamed@hamed-ThinkPad-T420:~$ iwconfig
lo        no wireless extensions.

wlan0     IEEE 802.11abgn  ESSID:"hossbitw"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: C8:6C:87:8C:44:DC   
          Bit Rate=1 Mb/s   Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=63/70  Signal level=-47 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:2  Invalid misc:119   Missed beacon:0

eth0      no wireless extensions.

hamed@hamed-ThinkPad-T420:~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 wlan0
192.168.1.0     0.0.0.0         255.255.255.0   U     1      0        0 eth0
192.168.1.0     0.0.0.0         255.255.255.0   U     2      0        0 wlan0
hamed@hamed-ThinkPad-T420:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:21:cc:5f:2e:4a  
          inet addr:192.168.1.51  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::221:ccff:fe5f:2e4a/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3969 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3484 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:4431969 (4.4 MB)  TX bytes:390643 (390.6 KB)
          Interrupt:20 Memory:f3900000-f3920000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:239 errors:0 dropped:0 overruns:0 frame:0
          TX packets:239 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:32005 (32.0 KB)  TX bytes:32005 (32.0 KB)

wlan0     Link encap:Ethernet  HWaddr a0:88:b4:55:05:08  
          inet addr:192.168.1.50  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::a288:b4ff:fe55:508/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:109 errors:0 dropped:0 overruns:0 frame:0
          TX packets:127 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:15458 (15.4 KB)  TX bytes:18287 (18.2 KB)

```

---

### Post by chili555 on 2012-04-28
> eth0      Link encap:Ethernet  HWaddr 00:21:cc:5f:2e:4a  
          [COLOR="Red"]inet addr:192.168.1.51[/COLOR]  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::221:ccff:fe5f:2e4a/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3969 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3484 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:4431969 (4.4 MB)  TX bytes:390643 (390.6 KB)
          Interrupt:20 Memory:f3900000-f3920000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:239 errors:0 dropped:0 overruns:0 frame:0
          TX packets:239 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:32005 (32.0 KB)  TX bytes:32005 (32.0 KB)

wlan0     Link encap:Ethernet  HWaddr a0:88:b4:55:05:08  
          [COLOR="Red"]inet addr:192.168.1.50[/COLOR]  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::a288:b4ff:fe55:508/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1Why are *both* ethernet and wireless connected? I can't see anything wrong aside from that.

---

### Post by hossub on 2012-04-28
because when my wireless connected ,i can't ping or use internet,my wireless adapter only get ip,then i am use my Ethernet to come here and send this message,then i am disable Ethernet.

---

### Post by hossub on 2012-04-28
i can connect to my wireless router and get ip,but i cant use internet or ping,
i dont have this problem in ubuntu 11.10

---

### Post by chili555 on 2012-04-28
Please reboot with the ethernet detached and then do:```
dmesg > hossub.txt
ifconfig >> hossub.txt
iwconfig >> hossub.txt
cat /etc/resolv.conf >> hossub.txt
ping -c3 192.168.1.1 >> hossub.txt
zip hossub.zip hossub.txt
```In your home directory, you will find a file called hossub.zip. Please attach it to your reply using the paperclip tool at the top of the reply box.

I love a mystery!

---

### Post by hossub on 2012-04-29
```
hamed@hamed-ThinkPad-T420:~$ dmesg > hossub.txt
hamed@hamed-ThinkPad-T420:~$ ifconfig >> hossub.txt
hamed@hamed-ThinkPad-T420:~$ iwconfig >> hossub.txt
lo        no wireless extensions.

eth0      no wireless extensions.

hamed@hamed-ThinkPad-T420:~$ cat /etc/resolv.conf >> hossub.txt
hamed@hamed-ThinkPad-T420:~$ ping -c3 192.168.1.1 >> hossub.txt
hamed@hamed-ThinkPad-T420:~$ zip hossub.zip hossub.txt 
  adding: hossub.txt (deflated 73%)
hamed@hamed-ThinkPad-T420:~$ 


```

---

### Post by chili555 on 2012-04-29
This is from /etc/resolv.conf:> # Dynamic resolv.conf(5) file for glibc resolver(3) generated by resolvconf(8)
#     DO NOT EDIT THIS FILE BY HAND -- YOUR CHANGES WILL BE OVERWRITTEN
[COLOR="Red"]nameserver 127.0.0.1[/COLOR]127.0.0.1 is the address of the localhost; that is, yourself. I don't understand where or why this happens. Please try this:```
sudo su
echo "nameserver 8.8.8.8" > /etc/resolv.conf
ping -c3 www.google.com
ping -c3 192.168.1.1
exit
```Did pings return?

Except for resolv.conf, everything looks perfect; the card associates without trouble:> [   25.296204] wlan0: authenticate with xx:6c:87:8c:44:xx (try 1)
[   25.298821] wlan0: authenticated
[   25.299106] wlan0: associate with xx:6c:87:8c:44:xx (try 1)
[   25.312016] wlan0: RX AssocResp from xx:6c:87:8c:44:xx (capab=0x411 status=0 aid=1)
[   25.312028] wlan0: associatedIt gets an IP address and a nice strong speed:> wlan0     Link encap:Ethernet  HWaddr xx:88:b4:55:05:xx 
          [COLOR="Red"]inet addr:192.168.1.50[/COLOR]  Bcast:192.168.1.255  Mask:255.255.255.0> wlan0     IEEE 802.11abgn  [COLOR="Red"]ESSID:"hossbitw"[/COLOR]  
          Mode:Managed  Frequency:2.412 GHz  Access Point: XX:6C:87:8C:44:XX   
          [COLOR="Red"]Bit Rate=135 Mb/s[/COLOR]   Tx-Power=15 dBm   Have you made any manual changes in Network Manager? Usually, they are unnecessary. Is this your home router? Anything unusual there?

---

### Post by hossub on 2012-04-29
```
hamed@hamed-ThinkPad-T420:~$ sudo su
[sudo] password for hamed: 
root@hamed-ThinkPad-T420:/home/hamed# echo "nameserver 8.8.8.8" > /etc/resolv.conf
root@hamed-ThinkPad-T420:/home/hamed# ping -c3 www.google.com
ping: unknown host www.google.com
root@hamed-ThinkPad-T420:/home/hamed# ping -c3 192.168.1.1
PING 192.168.1.1 (192.168.1.1) 56(84) bytes of data.

--- 192.168.1.1 ping statistics ---
3 packets transmitted, 0 received, 100% packet loss, time 2014ms


```

i don't change anything,before i have ubuntu 12.04, i have ubuntu 11.10 and ubuntu 11.10 work fine and i dont change anything , all are default

---

### Post by chili555 on 2012-04-29
May I see:```
cat /etc/resolvconf/interface-order
cat /etc/hosts
```Also, when you click the Network Manager icon and Edit Connections, under IPv6 is it set to Ignore? If not, please do. Disconnect and reconnect and try again:```
ping -c3 www.google.com
```Please see attached.

---

### Post by hossub on 2012-04-29
```
root@hamed-ThinkPad-T420:/home/hamed# cat /etc/resolvconf/interface-order
# interface-order(5)
lo.inet*
lo.dnsmasq
lo.pdnsd
lo.!(pdns|pdns-recursor)
lo
tun*
tap*
hso*
em+([0-9])?(_+([0-9]))*
p+([0-9])p+([0-9])?(_+([0-9]))*
eth*
ath*
wlan*
ppp*
*
root@hamed-ThinkPad-T420:/home/hamed# cat /etc/hosts
127.0.0.1	localhost
127.0.1.1	hamed-ThinkPad-T420

# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters

```

when i am ignore ipv6,i cant connect to wireless and i am chang it back but i cant connect,this is new problem i think your commands change something

---

### Post by hossub on 2012-04-29
i fix new problem,and remove wireless connection in  Network Manager and ignore ipv6 then:

```
root@hamed-ThinkPad-T420:/home/hamed# ping -c3 www.google.com
ping: unknown host www.google.com

```

---

### Post by chili555 on 2012-04-29
> i think your commands change somethingI doubt it. 'cat' simply reads out the file to the terminal so we can check it and, in your case, copy and paste it to the forum.

Your /etc/resolvconf/interface-order seems correct because it includes wlan* so that your wireless device gets recognized. I am troubled and am still studying about why wired works perfectly but wireless does not on the same machine.

---

### Post by hossub on 2012-04-29
ok tell my what i am must to do? and what your need

---

### Post by chili555 on 2012-04-29
Please check to see if the package resolvconf is installed:```
sudo dpkg -s resolvconf | head -n3
```I hope it says:> Package: resolvconf
[COLOR="Red"]Status: install ok[/COLOR] installed
Priority: optional
Now let's see if it's configured correctly.```
sudo dpkg --configure resolvconf
```We hope we see:> package resolvconf is already installed and configuredIf it does not, we may learn something from the message or, even better, the --configure may fix it.

This is a very interesting problem. I have at least two cases just like it.

---

### Post by hossub on 2012-04-29
```
hamed@hamed-ThinkPad-T420:~$ sudo dpkg -s resolvconf | head -n3
Package: resolvconf
Status: install ok installed
Priority: optional
hamed@hamed-ThinkPad-T420:~$ sudo dpkg --configure resolvconf
dpkg: error processing resolvconf (--configure):
 package resolvconf is already installed and configured
Errors were encountered while processing:
 resolvconf

```

---

### Post by chili555 on 2012-04-29
I need more time and more study. Back a bit later.

---

### Post by hossub on 2012-04-29
ok

---

### Post by Wlo on 2012-04-29
Am having same problem.  Thinkpad T420 upgraded last night from 11.10, now wireless connects but no traffic, ethernet is fine.

Have attached Hossub's suggested commands from earlier in the thread incase it's of any help.

Would be grateful for any assistance or pointers.

Thanks!

(output in attachment from:

dmesg > hossub.txt
ifconfig >> hossub.txt
iwconfig >> hossub.txt
cat /etc/resolv.conf >> hossub.txt
ping -c3 192.168.1.1 >> hossub.txt
)

---

### Post by chili555 on 2012-04-29
Will both of you try, without the ethernet cable attached:```
sudo modprobe -r iwlwifi
sudo modprobe iwlwifi 11n_disable=1
```Now try to connect the wireless and each give me a report.

I have a headache and her name is *iwlwifi*. What's very troubling is that I use the exact same wireless card trouble free.

---

### Post by Wlo on 2012-04-29
chili555 - after those commands wifi seems to work fine!  Thanks loads :)

What does that tell us then?

Thanks again :)

---

### Post by chili555 on 2012-04-29
I think that tells us that the iwlwifi driver isn't ready for N speeds; I suppose that if the router is trying to negotiate an N connection and the card can't do it, the card gives up and does nothing. One thing I do know is it's better to work than not work!!

To make this persistent, please do:```
sudo gedit /etc/modprobe.d/iwlwifi.conf
```A new empty file will open. Add one line:```
options iwlwifi 11n_disable=1
```Proofread, save and close gedit.

If you don't have gedit, use nano, leafpad, vim or any other text editor.

---

### Post by hossub on 2012-04-30
[SIZE="4"]thank you chili555,you are awesome[/SIZE]
:popcorn:

---

### Post by chili555 on 2012-04-30
I'm glad it's now working. Don't forget to write the conf file as above. Also, please use thread tools at the top and Mark Solved so the searchers will find out the solution.

---

### Post by hossub on 2012-04-30
ok,sure,if i have other problems,what is the best way for contact with you?

---

### Post by chili555 on 2012-04-30
> **hossub said:**
> ok,sure,if i have other problems,what is the best way for contact with you?It will be my pleasure to help you if I can at any time. Click my name and send me a private message and give me a link to the thread you've posted about your problem. I will help if I can.

---

### Post by nicholasc on 2013-03-22
I'm having a very similar issue.  I've went through the whole thread and I think this should include all of the information from before.  I'm aware this thread is a bit old, but my issue is too similar to ignore it.  I also made the changes to /etc/resolv.conf (adding 8.8.8.8 as the nameserver)

```
nick@nick-ThinkPad-W510:~$ cat /etc/resolvconf/interface-order 
# interface-order(5)
lo.inet*
lo.dnsmasq
lo.pdnsd
lo.!(pdns|pdns-recursor)
lo
tun*
tap*
hso*
em+([0-9])?(_+([0-9]))*
p+([0-9])p+([0-9])?(_+([0-9]))*
eth*
ath*
wlan*
ppp*
*
nick@nick-ThinkPad-W510:~$ cat /etc/hosts
127.0.0.1    localhost
127.0.1.1    nick-ThinkPad-W510

# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
nick@nick-ThinkPad-W510:~$ ping -c3 [www.google.com]("http://www.google.com")
PING [www.google.com]("http://www.google.com") (74.125.26.105) 56(84) bytes of data.

--- [www.google.com]("http://www.google.com") ping statistics ---
3 packets transmitted, 0 received, 100% packet loss, time 2016ms

nick@nick-ThinkPad-W510:~$ sudo dpkg -s resolvconf | head -n3
Package: resolvconf
Status: install ok installed
Priority: optional
nick@nick-ThinkPad-W510:~$ sudo dpkg --configure resolvconf
dpkg: error processing resolvconf (--configure):
 package resolvconf is already installed and configured
Errors were encountered while processing:
 resolvconf
nick@nick-ThinkPad-W510:~$ sudo modprobe -r iwlwifi
nick@nick-ThinkPad-W510:~$ sudo modprobe iwlwifi 11n_disable=1
nick@nick-ThinkPad-W510:~$ ping [www.google.com]("http://www.google.com")
PING [www.google.com]("http://www.google.com") (74.125.26.147) 56(84) bytes of data.
^C
--- [www.google.com]("http://www.google.com") ping statistics ---
6 packets transmitted, 0 received, 100% packet loss, time 5038ms
```

---

### Post by chili555 on 2013-03-24
> wlan0     Link encap:Ethernet  HWaddr 00:24:d7:9d:4f:c0  
          inet addr:[COLOR="#FF0000"]70.169.155.178[/COLOR]  Bcast:70.169.155.191  Mask:255.255.255.224
          inet6 addr: fe80::224:d7ff:fe9d:4fc0/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:848 errors:0 dropped:0 overruns:0 frame:0
          TX packets:125 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:93715 (93.7 KB)  TX bytes:14728 (14.7 KB)What explains this? Are you connected to the cable modem or to the router or...what?

---

### Post by nicholasc on 2013-03-24
I was actually dealing with some odd configurations.  I've been in a hotel for the last few days trying to deal with their wifi set up, but everything seems to be working now.  I'm just going to accept that and be happy. Thank you for responding though!

---

