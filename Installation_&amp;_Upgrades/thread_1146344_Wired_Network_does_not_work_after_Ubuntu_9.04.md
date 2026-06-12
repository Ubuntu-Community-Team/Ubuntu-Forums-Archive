---
title: "Wired Network does not work after Ubuntu 9.04"
date: 2009-05-02
forum: Installation &amp; Upgrades
---

### Post by gmemon on 2009-05-02
Hello,

I installed Ubuntu 9.04 (32 bit) yesterday. After that I cannot use the wired network anymore. The wireless worked like a charm. I cannot see the wired connection anywhere, neither in network monitor nor in ifconfig.

Any suggestions?

---

### Post by cariboo on 2009-05-02
Open an Applications-->Accessories-->Terminal and type:

```
sudo lshw -C network
```

the above command will list the details of all your network devices. Please paste the results in your next post.

---

### Post by gmemon on 2009-05-02
> **cariboo907 said:**
> Open an Applications-->Accessories-->Terminal and type:

```
sudo lshw -C network
```

the above command will list the details of all your network devices. Please paste the results in your next post.

Thanks for your reply. Following is the output:

```
sudo lshw -C network
  *-network               
       description: Wireless interface
       product: BCM4312 802.11b/g
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0c:00.0
       logical name: eth1
       version: 01
       serial: 00:16:44:c9:71:81
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl0 driverversion=5.10.79.10 ip=192.168.0.101 latency=0 module=wl multicast=yes wireless=IEEE 802.11bg
  *-network UNCLAIMED
       description: Ethernet controller
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: pm cap_list
       configuration: latency=64
  *-network DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: 22:cd:c6:2b:e0:56
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes

```
The ethernet controller seems to be unclaimed

---

### Post by gmemon on 2009-05-03
any suggestions?

---

### Post by bs_360 on 2009-05-05
I've run in the same issue:
- installed 9.04 (clean install, on a vmware vm) successfully
- able to use the network
- installed the latest updates (till today)
- reboot
- the network isn't working anymore

Here's my output

  *-network               
       description: Ethernet interface
       product: 79c970 [pc32lance]
       ...
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       ...

---

### Post by gmemon on 2009-05-06
I have also installed pre-release updates for Jaunty and still no luck. Has anyone solved this problem yet?

---

### Post by bs_360 on 2009-05-06
I've found that I'm still able to browse my lan (I can access through smb to a windows share)... but I'm not able to connect to internet (neither for surfing, nor for getting updates from repositories).
I'm using a proxy but I has the same settings that was working before installing the updates

---

### Post by rannday on 2009-05-06
You could make sure you installed a proper distribution. 

Use:

[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

I've installed Juanty Desktop-Edition and have had no network issues so far.

---

### Post by gmemon on 2009-05-06
I did an upgrade from 8.10 using the Update Manager. So the correct distribution should not be a problem?

My wireless connection works absolutely fine. Wired connection has problems

---

### Post by prodekan on 2009-05-06
I had the same problem this morning. I went to System>Preferences>Network Connections and in the "Wired" tab double-clicked "Auto eth0" and the typed my password in, changed _nothing_ in the settings just clicked apply and it optained the IP automaticly. And internet was back :)

---

### Post by gmemon on 2009-05-07
I cannot even see Auth eth0. I manually added eth0 but no luck :(

---

### Post by m5a5l3m on 2009-05-07
Mine is a fresh install and I don't see anything in my wiredConnection list.
Help please..

---

### Post by ReaderK on 2009-05-30
I raised this sort of problem against 8.10 back in February and there was some evidence that the problem had existed for quite some time.  Ubuntu replaced the "interfaces file" with "network manager" which appears to be a pile of <insert expletive of choice>. 

Oh and ours was a clean install of 8.10. So its not an upgrade issue. 

Solutions encountered:
1. uninstall network management (total bodge up) package
2a. use interfaces file - old technology works!
2b. use wicd instead - apparently it works and slackware include it so it must have **actually been tested** on more than one machine!

You got more replies than me - but no more help.  Another guy got the problem same weekend as me.  His solution - remove networking manager.  

Basically these forums have become microsoft-like.  No faults are allowed and even fewer get fixed!  As I say when I search in FEBRUARY the problems with network management were OLD NEWS but no fix.

---

