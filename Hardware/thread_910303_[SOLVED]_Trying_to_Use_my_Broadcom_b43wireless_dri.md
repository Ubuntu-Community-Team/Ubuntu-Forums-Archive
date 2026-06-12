---
title: "[SOLVED] Trying to Use my Broadcom b43wireless driver"
date: 2008-09-04
forum: Hardware
---

### Post by GabrielsHorn314 on 2008-09-04
I've been trying to use my wireless on my Compaq laptop, and I've seen that a lot of people are having problems with their b43 broadcom wireless card, but i haven't been able to help myself. I was wondering if anyone could help me with my situation because classes would be a lot better if my wireless worked on campus. thanks for the help in advance. Im running ubuntu 8.04 Hardy Heron

cory@cory-laptop:~$ lspci

03:02.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03)

cory@cory-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11g  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=27 dBm   
          Retry min limit:7   RTS thr: off   Fragment thr=2346 B   
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

---

### Post by GabrielsHorn314 on 2008-09-04
Any help?

---

### Post by Big_Kahunaca on 2008-09-12
[http://ubuntuforums.org/showthread.php?t=870575](http://ubuntuforums.org/showthread.php?t=870575)

Give this a try, it worked with my HP DV6404ca with the same card.  

(Skip to the part about Post Installation Setup, click the link in the broadcom section, run the script, and restart.  Worked like a charm for me.)

---

### Post by GabrielsHorn314 on 2008-09-13
thank you so much. that finally solved the problem

---

### Post by wowbuts5 on 2008-09-14
WoW  [wow gold](http://veryge.com/) in our special discounting zone of US servers is the most cheapest [world of warcraft gold](http://veryge.com/) in the world. On our 'buy now' page, you can buy wow gold of this special zone.And you will get gold within 5 minutes after ordered. Please click our "Fast gold order form" on the left hand . [ffxi gil](http://veryge.com/) Fast delivery within 5 minutes,7*24 services.

---

### Post by Big_Kahunaca on 2008-10-04
Excellent, glad it worked for you.

Could you mark this thread as [Solved] so that others might benefit from the fix.

---

