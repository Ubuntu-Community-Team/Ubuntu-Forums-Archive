---
title: "Wireless help for Presario C700"
date: 2008-01-23
forum: Hardware &amp; Laptops
---

### Post by NapsterX on 2008-01-23
i recently installed ubuntu onto my Presario C700 i did the wireless fix to enable the wifi again, but now i have a new problem with weak signals even while sitting next to a router it is only connecting 75% is there any type of fix to make connection stronger?

---

### Post by jeffus_il on 2008-01-23
You may have a problem and then you may not. The signal strength display is not accurate, different cards and drivers report different strengths, What are you comms like using the browser a distance away?

---

### Post by NapsterX on 2008-01-23
well at home the web browser works just fine but when i go to a plubic place such as starbucks and use there public wifi i am only connected at 25% and the internet doesn't work

---

### Post by NapsterX on 2008-01-23
by internet i meant web browser does work

---

### Post by jeffus_il on 2008-01-23
Try iwconfig in a terminal, see if you can see any errors, there are some counters in the output, the best signal strength comparison would be to compare the number you get for signal strength, to another machine of the same type, maybe a post.

---

### Post by NapsterX on 2008-01-23
napsterx@napsterx-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11g  ESSID:"linksys"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:16:B6:E5:96:4D   
          Bit Rate=54 Mb/s   Tx-Power:32 dBm   
          RTS thr:2347 B   Fragment thr:2346 B   
          Power Management:off
          Link Quality:60/100  Signal level:-57 dBm  Noise level:-96 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

---

### Post by jeffus_il on 2008-01-23
Your connection looks fine, 

Mine is working well at a distance and looks like this:
```
wlan0     IEEE 802.11b+/g+  ESSID:"linksys"  Nickname:"acx v0.3.36"
          Mode:Managed  Frequency:2.432 GHz  Access Point: 00:1A:70:47:8F:36   
          Bit Rate:36 Mb/s   Tx-Power=15 dBm   Sensitivity=1/3  
          Retry min limit:7   RTS thr:off   
          Power Management:off
          Link Quality=36/100  Signal level=10/100  Noise level=0/100
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:52  Invalid misc:0   Missed beacon:0
```

---

### Post by NapsterX on 2008-01-23
ok cool i guess i was just freaking out because i had a meeting today at a starbucks and the signal wasn't strong and the broswer wouldn't work but maybe it was just where i was sitting? i  don't really kno i plan on trying it out later today at a different location

---

### Post by jeffus_il on 2008-01-23
Good idea, Good Luck!

---

### Post by frandecai on 2008-05-08
Hi all, I' ve installed ubuntu 8.04 on this laptop but it doesn't recognize the wifi card. 
The output for the lspci command is:
01:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)

and the system has the madwifi drivers installed.


Help please!!

---

