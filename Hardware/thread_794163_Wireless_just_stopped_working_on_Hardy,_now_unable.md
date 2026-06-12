---
title: "Wireless just stopped working on Hardy, now unable to get back!"
date: 2008-05-14
forum: Hardware
---

### Post by srdempster on 2008-05-14
I have lost all wireless connection on my dell vostro 1000. First used ndiswrapper successfully to use my dell wlan1390 card, then that went pear-shaped.So used my Belkin usb wlan dongle with success and 54mbs.No I've lost wireless completely if I hover over gnome's applet in my panel it just shows wired connection only and if right-clicked enable wired it's ticked but wireless is unticked and greyed out?Here's my iwconfig output:

steve@steve-laptop:~$ iwconfig
lo no wireless extensions.

wmaster0 no wireless extensions.

wlan1 IEEE 802.11g ESSID:""
Mode:Managed Frequency:2.412 GHz Access Point: Not-Associated
Tx-Power=27 dBm
Retry min limit:7 RTS thrff Fragment thr=2346 B
Link Quality:0 Signal level:0 Noise level:0
Rx invalid nwid:0 Rx invalid crypt:0 Rx invalid frag:0
Tx excessive retries:0 Invalid misc:0 Missed beacon:0

wlan0 IEEE 802.11g ESSIDff/any
Mode:Managed Frequency:2.462 GHz Access Point: Not-Associated
Bit Rate:54 Mb/s Tx-Power:32 dBm
RTS thr:2347 B Fragment thr:2346 B
Power Managementff
Link Quality:0 Signal level:0 Noise level:0
Rx invalid nwid:0 Rx invalid crypt:0 Rx invalid frag:0
Tx excessive retries:0 Invalid misc:0 Missed beacon:0

eth0 no wireless extensions.

Any ideas?? This is a duplicate of a post on networking and wireless but have had no reply to it yet.I have ditched gnome network mangaer and got WICD on board which sees my wireless networks now, but still cannot connect.As if it cannot decrypt keys?

Steve
srdempster is online now Report Post   	Edit/Delete Message Reply With Quote Multi-Quote This Message Quick reply to this message Thanks
srdempster
View Public Profile
Send a private message to srdempster
Find More Posts by srdempster
Add srdempster to Your Contacts
New Reply

---

