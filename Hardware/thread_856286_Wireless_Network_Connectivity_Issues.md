---
title: "Wireless Network Connectivity Issues"
date: 2008-07-11
forum: Hardware
---

### Post by rustix on 2008-07-11
How do I connect to my wireless network? On windows, once I switch laptop on, it automatically detects and connects to my wireless network.. 

How do i connect to it using Ubuntu?

---

### Post by unoodles on 2008-07-11
First you need to check if you hardware has been detected.
open up a terminal and type iwconfig and post the results here.

Do you know the brand of wireless card? Is it Intel? Broadcom?

---

### Post by rustix on 2008-07-11
this is what i get 

```

rustix@rustix:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11g  ESSID:""  
          Mode:Managed  Channel:0  Access Point: Not-Associated   
          Tx-Power=0 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


```

This means its detected right? 
It's a Broadcom 802.11g wireless card

---

### Post by unoodles on 2008-07-11
It looks like its detected. Try looking in the top right corner of your screen near the clock and you should see the NetworkManager icon. Left click it and you should see a list of detected networks.

---

### Post by prophetski on 2008-07-11
i have a similar problem but it detects the connection but when i select it and type in the 26 character pass key it doesnt connect. it works no problem with windows

---

### Post by rustix on 2008-07-11
ahh it works now! turns out the drivers had not been installed :D

---

