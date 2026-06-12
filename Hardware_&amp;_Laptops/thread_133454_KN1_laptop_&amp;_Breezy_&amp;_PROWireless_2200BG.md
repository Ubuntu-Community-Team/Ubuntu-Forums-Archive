---
title: "KN1 laptop &amp; Breezy &amp; PRO/Wireless 2200BG"
date: 2006-02-20
forum: Hardware &amp; Laptops
---

### Post by Alf Stockton on 2006-02-20
On my Sahara KN1 laptop I am running Ubuntu Breezy and want to get my Intel(R) PRO/Wireless 2200BG Network Connection working:-

lsmod | grep ipw
ipw2200                92680  0
firmware_class          9472  1 ipw2200
ieee80211              27012  1 ipw2200
ieee80211_crypt         5636  2 ipw2200,ieee80211
alf@puppypad:~$  iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      unassociated  ESSID:"Stockton"
         Mode:Managed  Channel=0  Access Point: 00:00:00:00:00:00
         Bit Rate=0 kb/s   Tx-Power=20 dBm
         Retry limit:7   RTS thr:off   Fragment thr:off
         Power Management:off
         Link Quality:0  Signal level:0  Noise level:0
         Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
         Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.

Please tell me what I still need to do to get this working.

---

