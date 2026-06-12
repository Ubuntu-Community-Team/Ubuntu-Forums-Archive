---
title: "RaLink 2860STA EEEPC slow speeds"
date: 2009-01-23
forum: Hardware
---

### Post by dccrens on 2009-01-23
So I have the eeepc 1000H with ralink card, 160GB harddrive, 2GB ram and dual boot ubuntu 8.10 and windows xp. I have tried everything to get this "N" speed card to support "N" speeds but it always connects with a bitrate 54MB/s. It is like there is a setting that is locked. The signal strength is great! but the speed sucks. 

Output of iwconfig ra0 
ra0       RT2860 Wireless  ESSID:"xxxxxxxxxxx"  Nickname:"RT2860STA"
          Mode:Managed  Frequency=2.462 GHz  Access Point: xxxxxxxxxxxxxxx
          Bit Rate=54 Mb/s
          RTS thr: off   Fragment thr: off
          Encryption key: xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx
          Link Quality=100/100  Signal level:-42 dBm  Noise level:-81 dBm
          Rx invalid nwid: 0  Rx invalid crypt: 0  Rx invalid frag:0
          Tx excessive retries: 0  Invalid misc: 0   Missed beacon:0

Is there a way in ubuntu to change the bitrate?

---

### Post by nejode on 2009-01-24
Same problem here but with a Broadcom wireless... stuck at 54Mbps at home!

nelson@lenovo-laptop:~$ iwconfig wlan0
wlan0     IEEE 802.11bg  ESSID:"Delgado"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:1D:0F:XX:XX:XX   
          **Bit Rate=54 Mb/s**   Tx-Power=27 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality=85/100  Signal level:-46 dBm  Noise level=-71 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

It`s not the home wireless router because a desktop with a Atheros based card and an Acer laptop with an Intel based wireless work fine.

It`s not the Lenovo laptop (ofending machine) because the bitrate with the access point at work connects at 108Mbps...:confused:

---

### Post by dccrens on 2009-01-24
Well, it is definitely the drivers. There are several folks working on trying to improve and solve the issue. It pisses me off that the ASUS advertises working wireless-N but even under windows XP I can get no better than 64MP/s...

Someone should start a class action suit against ASUS for false advertising... :(

---

### Post by dccrens on 2009-06-17
{{{BUMP}}}

Anyone still looking at this? I have made no progress...

---

### Post by mynameinc on 2009-06-17
I am perfectly happy with 54Mbps... it does everything I need it to do, quickly.

---

### Post by dccrens on 2009-08-26
{{{BUMP}}} - Still poking along... I am amazed that no one has figured this out yet. I tried reinstalling the latest drivers but still no go... I am thinking perhaps the hardware itself is not really "draft N"...

---

