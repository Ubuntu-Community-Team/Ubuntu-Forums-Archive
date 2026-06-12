---
title: "AR9287 with ath9k limited to 10Mbit/s"
date: 2011-03-15
forum: Hardware
---

### Post by realdar on 2011-03-15
Hello,

i am pretty new here because i never had problem on ubuntu before this. 
Thanks everyone for  this.
I got a strange issue, my wifi is limited to 10MBit/s under ubuntu 10.10
under windows or with other computers i am at 22Mbit/s (both wifi and ethernet)

I tried kernel 2.6.35-22 , 2.6.35-27 and 2.6.35-28.
I tried :[FONT=monospace]
[/FONT]sudo apt-get install linux-backports-modules-compat-wireless-2.6.36-maverick-generic[FONT=monospace]
[/FONT]sudo apt-get install linux-backports-modules-compat-wireless-2.6.36-maverick-generic-pae[FONT=monospace]
[/FONT]sudo apt-get install linux-backports-modules-compat-wireless-2.6.36-maverick-server

i forced my router to be on 802.11g/b (i was before that with 802.11n but it changed nothing always 10Mbit/s)

sudo iwconfig wlan0
wlan0     IEEE 802.11bgn  ESSID:"home"  
          Mode:Managed  Frequency:2.442 GHz  Access Point: 00:23:8E:F6:8E:28   
          Bit Rate=54 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality=63/70  Signal level=-47 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

i tried deactivated ipv6 too.
I have tried a patched madwifi but module doesn't detect my hardware.

I don't know what to do next.
could you help me ?

---

