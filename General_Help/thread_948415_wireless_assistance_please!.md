---
title: "wireless assistance please!"
date: 2008-10-15
forum: General Help
---

### Post by Monolith1200 on 2008-10-15
Hello my name is Reno and unfortunatly im posting to you from a dominantly windows machine. I look at myself as a power user which has only inspired my getting into linux, but one thing holds me back... i have to opperate my internet exclusively wireless and my wireless card ( dynex enhanced wireless g desktop card DX-EBDTC) has had many problems being installed on ubuntu. The version of ubuntu i have to use is 8.04, if there is a better version to work with i would appreciate someone letting me know. 

 thanks much.

---

### Post by Kevbert on 2008-10-15
Welcome to Ubuntu.
In most cases it is necessary to download Linux firmware drivers or to install ndiswrapper so that you can use the native windows drivers.  To do this go to Applications-Accessories-Terminal and enter
```
lspci
iwconfig
```
Please post back the outputs from these.

---

### Post by Monolith1200 on 2008-10-15
i have a few more questions before i proceed. i thank you for your prompt answer.Well one is that i do a bit of gaming, i play battlefield 2142 and starcraft and id like to keep enjoying those two games. I know that WINE can emulate but id like to have the opperating system itself run the apps. 

             thanks much

---

### Post by Kevbert on 2008-10-16
It looks like Starcraft is being ported to run natively on Linux. Please look at this [[COLOR="Red"]post[/COLOR]]("http://ubuntuforums.org/showthread.php?t=547989"). I could not find anything for Battlefield 2142 apart from Linux server patches.

---

### Post by Daimoneze on 2008-10-22
I seem to be having the identical issue. This is a desktop machine with a Dynex PCI wireless device. Output of lspci is:
```
01:02.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)
```
and 
```
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

---

### Post by Monolith1200 on 2008-10-26
kevbert i appreciate all your help, i am now posting to you from an ibm t41 laptop 1.6 ghz pentium (r) M 512 mb ram ati radeoin mobile 7500 32mb. everything works dow nto the wireless and i was able to install everything thanks to you and some other tutorials. im so much happier with linux and will never return to windows.

---

