---
title: "Cannot use my wlan0 in ad-hoc mode"
date: 2008-07-28
forum: General Help
---

### Post by g0blin on 2008-07-28
Hi guy

I've a Lenovo R61 laptop with wireless chipset Intel Corporation PRO/Wireless 3945ABG Network Connection, that use the iwl3945 module and since when I've downloaded and installed the new kernel restricted modules (before with the 2.6.24-19 and now with the 2.6.24.20) I cannot use my wireless interfaces in ad-hoc mode.

I've wrote this commands:

```

iwconfig wlan0 mode ad-hoc
iwconfig wlan0 essid *essid-name*
iwconfig wlan0 channel 1

ifconfig wlan0 192.168.1.1 netmask 255.255.255.0
```

Then if I give a "iwlist scan" in a first time i can view the cell, something like this:

```
wlan0     Scan completed :
          Cell 01 - Address: 9A:33:08:BA:10:F2
                    ESSID:""
                    Mode:Ad-Hoc
                    Channel:2
                    Frequency:2.417 GHz (Channel 2)
                    Quality=0/100  Signal level=0 dBm  Noise level=0 dBm
                    Encryption key:off
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s; 1 Mb/s; 2 Mb/s
                              5.5 Mb/s; 11 Mb/s
                    Extra:tsf=0000000000000000
```


but without given ESSID, and after about 10 seconds the same command response to me:

```
wlan0     No scan results
```

Inside my syslog and doing a dmesg i can read:

```
[  666.122869] wlan0: Trigger new scan to find an IBSS to join
[  667.983042] wlan0: Creating new IBSS network, BSSID 9a:33:08:ba:10:f2
[  667.984326] wlan0: Configured IBSS beacon template based on scan results
[  696.398608] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[  710.614470] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[  725.738517] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
```

With 2.6.24-18 restricted modules all worked well. Have idea of what? Is it a bug?

Thanks in advance

Daniele

---

### Post by sibidiba on 2008-09-01
I have problems connecting a ThinkPad R61i to SonyEricsson P1i in AdHoc.

The same problems with no scan results and stange dmesg messages appear.

Probably an upstream bug in the wifi driver:

[http://www.intellinuxwireless.org/bugzilla/show_bug.cgi?id=1489](http://www.intellinuxwireless.org/bugzilla/show_bug.cgi?id=1489)

---

