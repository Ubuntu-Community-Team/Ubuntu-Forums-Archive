---
title: "Wireless information"
date: 2006-11-08
forum: Hardware &amp; Laptops
---

### Post by blueturtl on 2006-11-08
Hi.

Could someone point an intermediate Ubuntu user to the path of more knowledge?
I have an external 3COM USB wireless adapter that allows me to connect to our ADSL modem. It works straight up without any problems, but I have no idea how I'm supposed to monitor it. There is nothing in the tray or utilities that I've discovered that lets me see how good the connection quality is.

When I type iwconfig in the terminal I get this:

> wlan0     IEEE 802.11-DS  ESSID:"Spiderweb"  Nickname:"okuwlan"
Mode:Managed  Frequency:2.412 GHz  Access Point: 00:A0:C5:90:F5:59
Bit Rate:11 Mb/s   Tx-Power=15 dBm
Retry limit:8   RTS thr=1536 B   Fragment thr=1536 B
Power Management: off
Link Quality=0/0  Signal level=47/255  Noise level=0/0
Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
Tx excessive retries:0  Invalid misc:0   Missed beacon:0

Link Quality and Signal level seem to be those of interest, but I have no idea how to read that. Does Link Quality 0/0 really stand for anything? If signal level is 47/255 that's pretty bad right? Does someone know how to read this information?

---

### Post by happy-and-lost on 2006-11-08
There's a little app in the tray which looks like a blank screen (next to the clock), click on it and change what's in the box to wlan0

---

### Post by blueturtl on 2006-11-09
Hmm.. I don't have one. Is it a standard gnome-applet?

---

### Post by blueturtl on 2006-11-09
Ok, found it. I had to add one manually but it's there now. However when I right click and check properties it says signal strength is 0%. That can't be right, since I'm browsing using the very same wireless connection.

---

