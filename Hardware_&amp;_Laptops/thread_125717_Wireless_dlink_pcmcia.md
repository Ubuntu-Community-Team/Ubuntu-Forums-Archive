---
title: "Wireless dlink pcmcia"
date: 2006-02-04
forum: Hardware &amp; Laptops
---

### Post by ruvil on 2006-02-04
Hello!
How do i get my "Dlink airplus G DWL-G630" (H/W ver:E1) working on my IBM thinkpad 600?

---

### Post by moephan on 2006-02-04
ruvil,

I have a D-Link EL - G630 running on my dell laptop. After upgrading to Breezey it is navitely supported and simply shows up as interface ath0 in the Network settings program.

What did you try so far? Did starting up with it inserted?

Cheers, Rick

---

### Post by Devastator9 on 2006-03-22
I have the same card as the DWL-G630 and even did a new install of Breezy.
I see the wireless network in admin network. I even activated the card. I termail I did iwconfig and it shows no access point. 
Got any Ideas?

---

### Post by jml on 2006-03-22
A couple of ideas.  Is your access point set up to disply its SSID?  If not, did you set up the wireless card in your laptop to specifically connect to the SSID of your access point?

Another possible source of trouble is encryption.  First try setting up your access point and laptop to use an unencrypted network.  If that works then try adding WEP encryotion.  If that works, and you need WPA encryption, then you will need to download and configure wpa_supplicant on your laptop and set it to the parameters of your WPA encrypted access point since Ubuntu does not yet support WPA encryption.  Hope that this helps.

Joe

---

### Post by Devastator9 on 2006-03-23
Here is what I got from iwconfig 
ath0  IEE 802.11  ESSID: "XXXX"
Mode:Managed   Frequency:2.437 GHz  Access Point: 00:00:00:00:00:00
Bit Rate:1 Mb/s   Tx-Power: 18 dBm   Sensitivity=0/3
Retry:off    RTS thr:off  Fragment  thr:off
Power Management:off
Link Quality=0/94  Signal level=-95 dMb   Noise level=-95 dMb
Rx invalid nwid:0   Rx invalid misc:0  Rx invalid frag:0
Tx excessive retries:0   Invalid misc:0  Missed beacon:0

sit0  no wireless extensions.

Now what?
By the way THanks for the help.

---

