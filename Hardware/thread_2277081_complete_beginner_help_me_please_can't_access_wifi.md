---
title: "*complete beginner* help me please can't access wifi :'("
date: 2015-05-06
forum: Hardware
---

### Post by fade2 on 2015-05-06
Edit: Forgot to mention, I'm using Lubuntu.

Hi guys, just bought a cheap laptop off of ebay just for kids to browse internet.  I've decided to go against using Windows XP. Mainly because the laptop is old lol. It's an Acer Aspire 5050. AMD Turion 64, 1GB RAM.

Problem is, I can't wifi to work. I can get ethernet to work, but not the wifi. I've gone into network settings and *i think* I've set up the network right.

I've chosen +ADD

-WiFi-
SSID: *My network name*
Mode: adhoc
Band: Automatic
Device Mac: *blank*
Clone Mac: *blank*
MTU: Automatic

Network Encryption: WPA / WAP2 (Yes this is what it uses)
Password: *My password*

IPV4 - Auto
IPV6 - Auto


Any help is really appreciated <3

---

### Post by mcsheffrey on 2015-05-06
This is just a shot in the dark,  I've never used an acer laptop, but on my dell laptop the "F2" (with a pic of a transmitter tower on it) is also a toggle key for wifi, so even though you configure it correctly in ubuntu, this toggle must be on to enable wifi to work.

---

### Post by fade2 on 2015-05-06
Thanks for replying so quickly mcsheffrey. I'm glad to know I've got it set up correctly. I've pressed all Fn keys 3 times now and nothing other than switching my monitor on and off hahah.

---

### Post by fade2 on 2015-05-06
Somehow I'm getting the feeling that it's not even detecting the wifi on the laptop :(

fade@Fade:~$ sudo ifconfig wlan0 up
[sudo] password for fade: 
wlan0: ERROR while getting interface flags: No such device
fade@Fade:~$ sudo ifconfig wlan0
wlan0: error fetching interface information: Device not found

---

