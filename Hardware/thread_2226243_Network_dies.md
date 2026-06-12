---
title: "Network dies"
date: 2014-05-26
forum: Hardware
---

### Post by kdrejer on 2014-05-26
I have an issue that when my computer has been on for about 4 hours the network dies, I can't connect to anything. But if i reboot everything is working again, I have used manjaro where it was said that there might be some issue with power my network card, or something like that. 

```

kristoffer@kristoffer-U31SG:~$ iwconfigeth0      no wireless extensions.


lo        no wireless extensions.


wlan0     IEEE 802.11bgn  ESSID:"VIAguest"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: EC:44:76:81:77:71   
          Bit Rate=65 Mb/s   Tx-Power=16 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=51/70  Signal level=-59 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:15   Missed beacon:0


 
```

---

### Post by tgalati4 on 2014-05-26
It could be simple wireless interference.  Your signal is reasonably strong, but if you have a lot of antennas in your neighborhood, you will get dropped.

How many networks show up when you click on the wireless icon?

How many have 3 or 4 bars?  This indicates that you may have several, strong antennas near you.

How old is the machine?  Wireless chips do wear out.  They get hot and behave poorly.

Try rebooting the wireless router and moving the antenna to a better location.

A final option is to remove the battery from the laptop for an hour and let the wireless card reset its digital antenna trims.  Reseat the wireless card while you are at it.  Be careful of the antenna connections.  They are delicate.

I doubt your issue is specific to any version of Linux.  This sounds like a hardware problem.

---

