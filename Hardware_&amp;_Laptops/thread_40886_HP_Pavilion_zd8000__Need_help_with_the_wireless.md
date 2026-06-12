---
title: "HP Pavilion zd8000 : Need help with the wireless"
date: 2005-06-10
forum: Hardware &amp; Laptops
---

### Post by FizDev on 2005-06-10
Hmmm,
I have a HP Pavilion zd8000 and I can't seem to make my wireless card work properly. I've installed ndiswrapper with the drivers that Windows uses for my card (bcmwl5a.inf). I tried to configure it with iwconfig but everything I did had no effect, no matter what.
For example, if I try to set the ESSID:off/any, it remains ESSID:off/any! If it can help in anyway, this is what I get when I do 'iwconfig'
> wlan0     IEEE 802.11g  ESSID:off/any
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:00:00:00:00:00
          Bit Rate:54 Mb/s   Tx-Power:25 dBm
          RTS thr:2347 B   Fragment thr:2346 B
          Encryption key:off
          Power Management:off
          Link Quality:100/100  Signal level:-10 dBm  Noise level:-256 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
Has any of you guys been able to make it work? Any help would be great.

---

### Post by poiscas on 2005-06-28
hi fizdev,

I have the same problem, try that :

iwconfig wlan0 key s:my_key [1]
iwconfig wlan0 nickname mynickname
iwconfig wlan0 essid "my essid"
iwconfig wlan0 key restricted


h@ve a nice d@y

---

### Post by poiscas on 2005-06-28
Wifi (with only a wep key) under Zd8147ea works very well :

ndiswrapper 1.2
kernel 2.6.11 (be careful : no SMP kernel !!!)
win$ driver : bcmwl5a.inf
distrib : mandriva limited edition
(don't forget to switch off the firewall with mcc)

H@ve @ nice d@y !!

---

### Post by ianpeters on 2005-06-29
[QUOTE=FizDev]Hmmm,
I have a HP Pavilion zd8000 and I can't seem to make my wireless card work properly. I've installed ndiswrapper with the drivers that Windows uses for my card (bcmwl5a.inf). I tried to configure it with iwconfig but everything I did had no effect, no matter what.
For example, if I try to set the ESSID:off/any, it remains ESSID:off/any! If it can help in anyway, this is what I get when I do 'iwconfig'

Has any of you guys been able to make it work? Any help would be great.[/QUOTE]


Have you tried one of the HOWTOs floating around on the forum?

---

### Post by Lrodom on 2005-06-29
[check out this thread!  worked for me and I have ZD7000](http://ubuntuforums.org/showthread.php?t=25683) 

good luck might have to do the modprobe command after reboot.

---

### Post by raydr on 2005-07-31
[QUOTE=poiscas]Wifi (with only a wep key) under Zd8147ea works very well :

ndiswrapper 1.2
kernel 2.6.11 (be careful : no SMP kernel !!!)
win$ driver : bcmwl5a.inf
distrib : mandriva limited edition
(don't forget to switch off the firewall with mcc)

H@ve @ nice d@y !![/QUOTE]


Wait. Are you saying I cannot use the SMP kernel in order for the wireless to work?

Please confirm this!

---

