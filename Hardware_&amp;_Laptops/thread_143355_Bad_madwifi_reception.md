---
title: "Bad madwifi reception"
date: 2006-03-12
forum: Hardware &amp; Laptops
---

### Post by thecwin on 2006-03-12
Recently I moved my laptop from Gentoo to Ubuntu. It's great, everything works perfectly including Xgl except for my wireless card which has a minor problem-- awful signal quality. 

Maybe something coincidental happened to my router inbetween upgrading from Gentoo to Ubuntu, or someone introduced a noisy device, but I'm sitting about 2m away from it and I've got only 40% signal strength and it's disassociating itself with the AP every minutes or so. I tried setting it up manually and tried network-manager and I get the same problem in both. 

It's not just the lights on the network card malfunctioning either since any data trasnfer will stop during the time it's blinking. If I put it about 20cm away from the router it's fine.. I've checked it's arial and all that.. can't see any problems.
Gentoo with my own kernel+madwifi(-ng) was fine all the way at the opposite side of the house with better signal strength than I'm getting... so... any ideas? Maybe Ubuntu sets it up with different TX power or sensitivity but I don't know a great deal about how wireless works or what it was set to in Gentoo, so I can't really figure it out.

**Details of hardware**
Netgear WG511T with Atheros chipset.

```

ath0      IEEE 802.11g  ESSID:"XTREME"
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:09:5B:DF:D3:B6
          Bit Rate:36 Mb/s   Tx-Power=15 dBm   Sensitivity=0/3
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=44/94  Signal level=-51 dBm  Noise level=-95 dBm
          Rx invalid nwid:4  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:18  Invalid misc:18   Missed beacon:1

```

```

cwin@laptop:~$ dmesg | grep "ath"
[4294685.012000] ath_hal: module license 'Proprietary' taints kernel.
[4294685.013000] ath_hal: 0.9.14.9 (AR5210, AR5211, AR5212, RF5111, RF5112, RF2413)
[4294685.088000] ath_rate_sample: 1.2
[4294685.095000] ath_pci: 0.9.6.0 (EXPERIMENTAL)
[4294685.514000] ath0: 11b rates: 1Mbps 2Mbps 5.5Mbps 11Mbps
[4294685.514000] ath0: 11g rates: 1Mbps 2Mbps 5.5Mbps 11Mbps 6Mbps 9Mbps 12Mbps 18Mbps 24Mbps 36Mbps 48Mbps 54Mbps
[4294685.514000] ath0: turboG rates: 6Mbps 9Mbps 12Mbps 18Mbps 24Mbps 36Mbps 48Mbps 54Mbps
[4294685.514000] ath0: H/W encryption support: WEP AES AES_CCM TKIP
[4294685.514000] ath0: mac 5.9 phy 4.3 radio 4.6
[4294685.514000] ath0: Use hw queue 1 for WME_AC_BE traffic
[4294685.514000] ath0: Use hw queue 0 for WME_AC_BK traffic
[4294685.514000] ath0: Use hw queue 2 for WME_AC_VI traffic
[4294685.514000] ath0: Use hw queue 3 for WME_AC_VO traffic
[4294685.514000] ath0: Use hw queue 8 for CAB traffic
[4294685.514000] ath0: Use hw queue 9 for beacons
[4294685.514000] ath0: Atheros 5212: mem=0x22000000, irq=5
[4294714.317000] ath0: no IPv6 routers present
[4294818.374000] ADDRCONF(NETDEV_UP): ath0: link is not ready
[4294820.645000] ADDRCONF(NETDEV_CHANGE): ath0: link becomes ready
[4294841.142000] ath0: no IPv6 routers present

```

---

### Post by zygous on 2006-11-16
I'm experiencing the same problem, also using a WG511T. Did you manage to solve it?

I've just installed ndiswrapper to try that for a while instead, but I'd prefer to get madwifi working so that I can actually see some signal quality metrics. Also, NetworkManager isn't likely to do roaming properly using ndiswrapper, is it...?

Cheers,

Richard.

---

### Post by spotman on 2007-01-06
Hi there,

I also have this problem, and was curious if anyone resolved this yet..

fwiw, there is another thread going on here:

[http://ubuntuforums.org/showthread.php?t=305491](http://ubuntuforums.org/showthread.php?t=305491)

Very strange deal...  I can reboot to my windows install on another hard disk, and the same card reception to the same router is 95%, but in edgy its hovering around 25%...

I have tried the latest madwifi from svn with no dice.  I wonder if its just an option that has been default set somewhere, but I can't seem to find it.  

cheers, and thanks for any light anyone might be able to shed...

---

