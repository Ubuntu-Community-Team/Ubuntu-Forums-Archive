---
title: "Sager 9880 Ethernet Woes"
date: 2005-06-09
forum: Hardware &amp; Laptops
---

### Post by clarke.rainey on 2005-06-09
Well I just dropped a bunch of cash on a 9880 and for the most part I am very happy with it... the only problems are that for some reason the Ethernet is very very slow and stalls, the wireless does not work, and the sound does not work...

Now I am sure that I can fix all of these problems if I can get the ethernet so it does not stall...

I got this

```
odin@Asgard:~$ lspci | grep [eE]thernet 0000:0a:03.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8169 Gigabit Ethernet (rev 10)
0000:0a:05.0 Ethernet controller: Linksys, A Division of Cisco Systems [AirConn] INPROCOMM IPN 2220 Wireless LAN Adapter (rev 01)
``` 

and everything else is the ubuntu hoary default from the disk as I have not really been able to download anything...

I am however typing this from that laptop using the ethernet... that is what confuses me...

If anyone could help me it would be very helpful...

here is a link to the system...

[HTML]http://www.pctorque.com/9880.php[/HTML] 

I got the system with the intel 630 CPU... and Nvidia 6800 Ultra...

---

### Post by clarke.rainey on 2005-07-03
Well the Ethernet was sorta working for while but would only give me speeds slower than a 28.8 modem and would often time out... I did get my wireless working using ndis wrapper and I also got my sound to work...

I have recently tried to get the Realtek drivers for this network chipset from their website in an attempt to get it working properly it become totally inoperable after the next reboot... I have tried reinserting the r8169.ko module but it gives me this message...

```
odin@Asgard:/lib/modules/2.6.10-5-686-smp/kernel/drivers/net$ sudo insmod r8169.ko
Password:
insmod: error inserting 'r8169.ko': -1 Unknown symbol in module
``` 

I am not at a complete loss of ideas and I am a newbie that apparently knows just enough to destroy his machine... any help would be very much appreciated...

---

