---
title: "caps lock blinking crash with madwifi."
date: 2010-02-09
forum: Hardware
---

### Post by vpnm_87 on 2010-02-09
Hi,
  I have Atheros AR5008X mini PCI express card in my DELL Studio 1535 laptop..am running Ubuntu 8.10..

I blacklisted ath9k driver and compiled n installed madwifi from the svn trunk...

I am getting this error often in 

```
/var/log/syslog
 wifi0: ath_fatal_tasklet: Hardware error; resetting.

```

Anyone got idea about above error??
My wireless internet connection works fine amidst the above error..

When i try to put my card in monitor mode with below steps:

```
$sudo ifconfig ath0 down

$sudo wlanconfig ath0 destroy

$sudo wlanconfig ath0 create wlandev wifi0 wlanmode monitor
```
The output came as "ath0"

We checked the mode using iwconfig command..it showed "monitor"

```
$sudo ifconfig ath0 up

```
After few seconds my **Caps Lock LED started blinking and Ubuntu crashed**..

I repeated the steps after rebooting and ended up in same crash..

When i tried to put in "sta"(station) mode using wlanconfig i didnt face any crash..

I just want to know whether the crash is due to 

1) Ubuntu 8.10 
2) madwifi Driver
3) Atheros AR5008X hardware

---

### Post by vpnm_87 on 2010-02-14
Solved the issue by uninstallin madwifi latest svn version and installin "madwifi-hal-testing"..

Now no crash, no capslock blinking..monitor mode works fine..no errors in /var/log/syslog....

---

