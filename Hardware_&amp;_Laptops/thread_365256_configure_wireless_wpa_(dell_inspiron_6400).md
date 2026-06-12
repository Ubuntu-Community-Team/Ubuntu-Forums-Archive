---
title: "configure wireless wpa (dell inspiron 6400)"
date: 2007-02-19
forum: Hardware &amp; Laptops
---

### Post by eldersoares on 2007-02-19
im trying to configure wpa according to this howto [https://help.ubuntu.com/community/WifiDocs/WPAHowTo](https://help.ubuntu.com/community/WifiDocs/WPAHowTo)

the first problem is that i didnt have a wpa_supplicant.conf... well, i found one inside a gz file and i uncompressed to etc dir.

then, when i tested with
 sudo wpa_supplicant -iath0 -c/etc/wpa_supplicant.conf -Dmadwifi -w

appeared this:
ioctl[SIOCSIWPMKSA]: No such device
ioctl[SIOCSIWMODE]: No such device
Could not configure driver to use managed mode
ioctl[SIOCGIFFLAGS]: No such device
Could not set interface 'ath0' UP
ioctl[SIOCGIWRANGE]: No such device
ioctl[IEEE80211_IOCTL_SETPARAM]: No such device
ioctl[SIOCSIWAP]: No such device
ioctl[SIOCGIFFLAGS]: No such device
Failed to initialize driver interface

so... what can i do?!??!
thanks!

---

### Post by sdide on 2007-02-19
what does (run as root)
# iwconfig 
output?

---

### Post by eldersoares on 2007-02-19
hello!
the output is

lo        no wireless extensions.

eth0      no wireless extensions.

eth1      unassociated  ESSID:off/any  
          Mode:Managed  Frequency=nan kHz  Access Point: Not-Associated   
          Bit Rate:0 kb/s   Tx-Power:16 dBm   
          Retry limit:15   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:14763   Missed beacon:0

sit0      no wireless extensions.


thanks!

---

### Post by n00bish on 2007-02-19
> **eldersoares said:**
> hello!
the output is

lo        no wireless extensions.

eth0      no wireless extensions.

eth1      unassociated  ESSID:off/any  
          Mode:Managed  Frequency=nan kHz  Access Point: Not-Associated   
          Bit Rate:0 kb/s   Tx-Power:16 dBm   
          Retry limit:15   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:14763   Missed beacon:0

sit0      no wireless extensions.


thanks!

One problem is you're using ath0 for wireless when your wireless adapter is labled "eth1".   Try running it with that changed and see what happens.

---

### Post by sdide on 2007-02-20
I would try the line.

```
$ sudo wpa_supplicant -ieth1 -c/etc/wpa_supplicant.conf -Dmadwifi -w
```

---

### Post by wieman01 on 2007-02-20
> **eldersoares said:**
> im trying to configure wpa according to this howto [https://help.ubuntu.com/community/WifiDocs/WPAHowTo](https://help.ubuntu.com/community/WifiDocs/WPAHowTo)

the first problem is that i didnt have a wpa_supplicant.conf... well, i found one inside a gz file and i uncompressed to etc dir.

then, when i tested with
 sudo wpa_supplicant -iath0 -c/etc/wpa_supplicant.conf -Dmadwifi -w

appeared this:
ioctl[SIOCSIWPMKSA]: No such device
ioctl[SIOCSIWMODE]: No such device
Could not configure driver to use managed mode
ioctl[SIOCGIFFLAGS]: No such device
Could not set interface 'ath0' UP
ioctl[SIOCGIWRANGE]: No such device
ioctl[IEEE80211_IOCTL_SETPARAM]: No such device
ioctl[SIOCSIWAP]: No such device
ioctl[SIOCGIFFLAGS]: No such device
Failed to initialize driver interface

so... what can i do?!??!
thanks!
Can you connect to unsecured networks at all?

---

