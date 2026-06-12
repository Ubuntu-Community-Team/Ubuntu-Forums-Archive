---
title: "Asus A53E/K53E wifi troubles"
date: 2011-10-24
forum: Hardware
---

### Post by dbulow on 2011-10-24
My sister's laptop is able to scan for wifi networks out of the box with her intel centrino 6300 agn card, but she can not connect to my home network, i have the same card in my toshiba portege r835 and i can connect. when she tries connecting on windows it works, but on ubuntu if she tries connecting it just asks her for the password, then waits a bit, then asks again. i have tried recompiling the compat wifi drivers but to no avail this is the output of iwconfig on her machine
```
ziva@ziva-K53E:~$ iwconfig 
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11abg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off

```i have worked for hours on this and am 100% stumped, any help would be appreciated.

---

