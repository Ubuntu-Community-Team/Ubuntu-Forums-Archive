---
title: "Centrino Ultimate-N 6300 and half speed"
date: 2020-11-30
forum: Hardware
---

### Post by fluca1978 on 2020-11-30
Hi all,
I'm going mad on this: I've my thinkpad T410 running on wireless network at home. I cannot get the full networking speed, first of all here is my wifi card:

```

% lshw -class network
...
*-network
       description: Wireless interface
       product: Centrino Ultimate-N 6300
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wlp3s0
       version: 35
       serial: 00:24:d7:24:bf:8c
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwlwifi driverversion=5.3.0-64-generic firmware=9.221.4.1 build 25532 ip=192.168.1.2 latency=0 link=yes multicast=yes wireless=IEEE 802.11
       resources: irq:31 memory:f2400000-f2401fff


```

and the network speed it should be on is:


```

% iwconfig
wlp3s0    IEEE 802.11  ESSID:"SOFIA"  
          Mode:Managed  Frequency:5.26 GHz  Access Point: EE:FD:73:BF:79:BC   
          Bit Rate=243 Mb/s   Tx-Power=15 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=46/70  Signal level=-64 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:1101   Missed beacon:0



```

but doing a speed test does not give me more than 60Mbps in download and 20 Mbps in upload. What is worst, while other network adapter are receiving the signal fine where the pc is, this one is not getting a good signal if I don't move the router in a particular position, that is why I believe this adapter is either working bad or is misconfigured.

My system is:

```

% lsb_release -a
No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 19.10
Release:        19.10
Codename:       eoan


```

I've found several discussions on this particular adapter, but they referred to ubuntu 12.06 and are stating to modify the ```
/etc/modprobe.d/iwlwifi.conf
``` file to contain the options

```

options iwlwifi 11n_disable=8

```

that I have tried without any success. I've already turned off powersave mode. The bluetooth adapter is turned off.
I've also tried to mve the above options into a file ```
/etc/modprobe.d/iwlwifi11n.conf
``` and rebooted, but at first I got no change at all, while after a fulle power off I was running on 3 Mbps and iwconfig was showing 56 Mbps. I then removed the ```
iwlwifi11n.conf
``` file and halted the system, and now I'm again on 56 Mpbs up to 60 Mbps while iwconfig keep telling me I'm at more than 200 Mbps.

Is there something I can do to get out every single bit about this network adapter?

---

### Post by fluca1978 on 2020-12-03
I've tried another parameter in */etc/modprobe.d/iwlfi11n.conf* as follows:

```

options iwlwifi bt_coex_active=0 swcrypto=1 11n_disable=8

```

without any success. I've also noted that the bit rate reported by iwconfig does not seem to be influenced by the link qualityy.
Any suggestion?

---

### Post by CelticWarrior on 2020-12-03
```
[COLOR=#000000][FONT=&quot]Description:    Ubuntu 19.10[/FONT][/COLOR]
```

Ubuntu 19.10 is EOL. Please do your backups and install a supported release. I would recommend Ubuntu 20.04 because it has extended support of 5 years.
There's no point in troubleshooting an EOL release. Please come back to the matter if and only the same issue is present in a freshly 20.04.

---

