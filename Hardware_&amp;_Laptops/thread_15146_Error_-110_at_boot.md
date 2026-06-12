---
title: "Error -110 at boot"
date: 2005-02-12
forum: Hardware &amp; Laptops
---

### Post by jorgerg on 2005-02-12
Hello,
at boot, got a message "error -110 setting multicast list". Could someone tell me where to go for information about it (causes, consequences, solutions, etc)? Please do not be too much cryptic (i'm a very very real newbie).
Thnx

---

### Post by alastair on 2005-02-12
It's a netwoking error. A google for "error -110 setting multicast list" will gibve you some idea of the scope.

Not sure I know what the problem is - is it wireless? A chipset or driver problem.

First rule of asking for tech support is - there is no such thing as too much information!

So, if you want help you should include more info e.g.

ifconfig -a

errors from log files (not the whole files) e.g.

/var/log/syslog

Any other information e.g. network setup, make of network device/card etc.

---

### Post by jorgerg on 2005-02-13
Yes, definitely right, i should have give more information! 
I've been at Google looking for this message and - apparently - it seems related to the DWL-G650 wireless PCMCIA card. (which i'm using).
I've also took a deep look into the Networking Forum for this card specific problems. But, unless many other people, i did not have any problems connecting with it.  The card was inside when i first installed Ubuntu Warty (about a week ago), asked me if i wanted to use it as eth0 (said yes), asked me automatically for a WEP key (which was actually used by my router) and did work since the very first moment! I have to say that i was very impressed by this distro!
So, i keep on having the same message at every boot but the card works very well, with the original information and also when i change parameters (like no more keys for public places) with System Conf -> Networking.
Here below are some outputs to help understanding the problem, but please be aware that i have no fonctional problems, i just keep on having that message and i do not know it cause, consequences and solution.
Thnx a lot for your help.
*********************************
ifconfig:
eth0      
Lien encap:Ethernet  HWaddr NN:NN:NN:NN:NN:NN
inet adr:192.168.0.100  Bcast:192.168.0.255  Masque:255.255.255.0
adr inet6: fe80::220:e0ff:fed0:b5a8/64 Scope:Lien
UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
RX packets:428 errors:0 dropped:0 overruns:0 frame:0
TX packets:16 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 lg file transmission:1000 
RX bytes:137041 (133.8 KiB)  TX bytes:2925 (2.8 KiB)
Interruption:10 Adresse de base:0x1000 Mémoire:f0401000-f0401fff 

iwconfig:
eth0      
IEEE 802.11-DS  ESSID:"xxxxx"  Nickname:"Prism  I"          
Mode:Managed  Frequency:2.437GHz  Access Point: NN:NN:NN:NN:NN:NN           
Bit Rate:11Mb/s   Tx-Power=15 dBm   Sensitivity:1/3            
Retry min limit:8   RTS thr:off   Fragment thr:off           
Power Management:off           
Link Quality=82/92  Signal level=-11 dBm  Noise level=-145 dBm           
Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0           
Tx excessive retries:0  Invalid misc:0   Missed beacon:0 

/var/log/syslog:
Feb  5 16:24:18 localhost kernel: eth0: Station identity 000f:0000:0001:0005
Feb  5 16:24:18 localhost kernel: eth0: Looks like an Intersil firmware version 1.5.6
Feb  5 16:24:18 localhost kernel: eth0: Ad-hoc demo mode supported
Feb  5 16:24:18 localhost kernel: eth0: IEEE standard IBSS ad-hoc mode supported
Feb  5 16:24:18 localhost kernel: eth0: WEP supported, 104-bit key
Feb  5 16:24:18 localhost kernel: eth0: MAC address NN:NN:NN:NN:NN:NN
Feb  5 16:24:18 localhost kernel: eth0: Station name "Prism  I"
Feb  5 16:24:18 localhost kernel: eth0: ready
Feb  6 09:11:09 localhost kernel: ath_hal: module license 'Proprietary' taints kernel.
Feb  6 09:11:09 localhost kernel: ath_hal: 0.9.11.6
Feb  6 09:11:09 localhost kernel: wlan: 0.8.4.2 (EXPERIMENTAL)
Feb  6 09:11:09 localhost kernel: ath_pci: no version for "ieee80211_ioctl_siwrate" found: kernel tainted.
Feb  6 09:11:09 localhost kernel: ath_pci: 0.9.4.0 (EXPERIMENTAL)
Feb  6 09:11:09 localhost kernel: PCI: Enabling device 0000:02:00.0 (0000 -> 0002)
Feb  6 09:11:09 localhost kernel: ath0: 11b rates: 1Mbps 2Mbps 5.5Mbps 11Mbps
Feb  6 09:11:09 localhost kernel: ath0: 11g rates: 1Mbps 2Mbps 5.5Mbps 11Mbps 6Mbps 9Mbps 12Mbps 18Mbps 24Mbps 36Mbps 48Mbps 54Mbps
Feb  6 09:11:09 localhost kernel: ath0: mac 5.9 phy 4.3 5ghz radio 4.6
Feb  6 09:11:09 localhost kernel: ath0: 802.11 address: NN:NN:NN:NN:NN:NN
Feb  6 09:11:09 localhost kernel: ath0: Use hw queue 0 for WME_AC_BE traffic
Feb  6 09:11:09 localhost kernel: ath0: Use hw queue 1 for WME_AC_BK traffic
Feb  6 09:11:09 localhost kernel: ath0: Use hw queue 2 for WME_AC_VI traffic
Feb  6 09:11:09 localhost kernel: ath0: Use hw queue 3 for WME_AC_VO traffic
Feb  6 09:11:09 localhost kernel: ath0: Atheros 5212: mem=0x1e800000, irq=10
...
Feb  6 09:11:09 localhost kernel: eth0: Error -110 setting multicast list.
Feb  6 09:11:09 localhost kernel: eth0: Error -110 setting multicast list.
Feb  6 09:11:09 localhost kernel: eth0: New link status: Connected (0001)
...
Feb  6 09:16:40 localhost kernel: eth0: error -5 reading Rx descriptor. Frame dropped.

it also appears in dmesg:
eth0 - Error -110 setting multicast list

************************************

---

### Post by alastair on 2005-02-13
Thanks fo rthe extra information. I cannot really help, I'm sorry. I have been in similar situations in the past however - perhaps someone else can help.

However - you say the card works? Then this "error" in the logs is not so bad and might get fixed in a release or two of the kernel or driver (which appears to be proprietary?). It might also be worth asking on one of the Linux newsgroups (linux networking one for instance).

If you get any real problems, come back :-)

---

