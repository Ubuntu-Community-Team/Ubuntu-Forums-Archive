---
title: "Broadcom kernel panic no connectivity with B43"
date: 2011-12-28
forum: Hardware
---

### Post by hookum on 2011-12-28
I recently moved into an apartment building which provides free wifi, allowing me to finally be rid of Clearwire. I went out and bought a Netgear WN311B PCI wireless card, and it works perfectly with WinXP (go figure...). However, with Kubuntu I'm not so lucky.

The Broadcom STA wireless drivers ( bcmwl-kernel-source-5.100.82.38+bdcom-0ubuntu4 ) connect me to the wireless network fine, work great, except I get a kernel panic after about 30-60 seconds, with random data dumped. Not very usable.

The B43 drivers ( firmware-b43-installer-1:014-9 and b43-fwcutter-1:014-9 ) load properly and WLAN interface is displayed under the Network Management systray icon. However, it cannot detect any networks. 

Using ndiswrapper and the drivers from my Windows installation, WLAN is NOT displayed under Network Management, nor is wlan0 listed from iwconfig

Any help resolving this issue would be greatly appreciated.

Kubuntu version: 11.10
Kernel: 3.0.0-12

with B43
-------------------------------------------------------------
```

iwconfig 
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off

ping -c 3 192.168.1.1
connect: Network is unreachable


lsmod | grep b43
b43                        341198  0 
ssb                        52752  1 b43
mac80211              310872  1 b43
cfg80211                199587  2 b43,mac80211

```with ndiswrapper
------------------------------------------------------------------
```

lsmod | grep ndiswrapper
ndiswrapper           254773  0 

iwconfig 
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      no wireless extensions.

ndiswrapper -l
wn311b : driver installed
        device (14E4:4329) present (alternate driver: ssb)

```

---

### Post by hookum on 2011-12-30
I forgot to mention - in fact, I forgot altogether - that I was running a 64-bit installation. After reading pytheas22's guide here:

 [http://ubuntuforums.org/showthread.php?t=885847](http://ubuntuforums.org/showthread.php?t=885847) 

specifically check #2, I decided this was my problem. I reinstalled a fresh 32-bit 11.10 release, and the Broadcom STA drivers work perfectly - no more kernel panics.

---

