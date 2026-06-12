---
title: "Recommend Gigabit network card for 64 Bit Ubuntu 8.10"
date: 2008-11-19
forum: Hardware
---

### Post by icpeanuts on 2008-11-19
I have no luck with getting my Intel desktop Pro gigabit card to work with 8.10 Ubuntu 64 bit.

In the mean time, please post Which brand/model PCI Gigabit network card will work out of the box with Ubuntu 8.10 64 bit.

Thanks

---

### Post by m_l17 on 2008-11-19
I use Netgear GA311. Ubuntu 8.10 recognized with no problems and runs at 1000Mbps :) I bought mine from BestBuy a few months back for around $20

> ml ~ $  ifconfig
Link encap:Ethernet  HWaddr 78:a4:38:54:99:21
          inet addr:192.168.1.101  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: lk58::54d:7kkl:aj45:6369/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:146668 errors:0 dropped:0 overruns:0 frame:0
          TX packets:110433 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 [COLOR="Red"]txqueuelen:1000[/COLOR] 
          RX bytes:183850171 (183.8 MB)  TX bytes:15368888 (15.3 MB)
          Interrupt:18 Base address:0xe000

---

### Post by icpeanuts on 2008-11-19
Are you using ubuntu 64 bit version? Thanks

---

### Post by m_l17 on 2008-11-19
Yes, and sorry for leaving that out :redface:

> ml ~ $  uname -a
Linux amd64 2.6.27-7-generic #1 SMP Tue Nov 4 19:33:06 UTC 2008 x86_64 GNU/Linux

---

### Post by IanW on 2008-11-19
IIRC that Intel gigabit cards were "locked out" during Intrepid's Beta phase, as their firmware was being overwritten/corrupted.

I think that this has now been fixed and the cards "unlocked" by now, though.

---

### Post by icpeanuts on 2008-11-19
I just ordered Netgear GA311. Thanks

I heard about the Intel gigabit formware issue during pre release. The 32 bit version of Ubintu works fine with the Intel card, but after I installed the 64 bit version, I can not connect to the Network. The net detecting apps just keep disconnecting, few seconds later, connecting. The green dot just keep going. I tried assigning it static ip, same thing. It does not work. I tried posting on the forum, no one answer.

I am having problem with it on the 64 bit Ubuntu.  I love the Intel card, they work really well. I just can not imagine that it not working on Ubuntu 64 bit.

Thanks for all the suggestions.

---

