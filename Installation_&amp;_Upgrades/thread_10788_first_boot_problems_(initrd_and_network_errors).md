---
title: "first boot problems (initrd and network errors)"
date: 2005-01-11
forum: Installation &amp; Upgrades
---

### Post by sas on 2005-01-11
I've installed my system following the knoppix installation how to, rebooted and now i get three "failures" when the system is trying to start linux. It seems to just carry on anyway, however after it reaches "ipv6 via ipv4 tunneling" or something it just stops, I then can't do anything except reboot.

The three failures I get are:
"can't find initrd device"
"configuration of network interfaces"
"temporary failure in name resolution"

I presume the problem is related to the first failure?

Thanks for any help, I look forward to using Ubuntu.
Yours,
Dean

---

### Post by SnoZ on 2005-01-11
i never seen that, still im newbie in ubuntu or any other linux distribution, but i think someone or even i could help a bit more if you could tell us your hardware devices, like your VGA or something...  :/

---

### Post by sas on 2005-01-11
sorry, i'll try to include anything i think that is relevant...
everything on my system is nforce2, with the exception of my wifi adapter and bluetooth device (neither of which i use)

everything works in knoppix 

i have a initrd entry in /dev
i have initrd.img files in / (symlinking to files in /boot) 
i have initrd entries in grub.conf pointing towards the symlinks in /

my initrd files have the same version as my kernel does.

I forgot to mention that i can ping and everything fine while chrooted into my install....
My hosts file:
127.0.0.1       localhost
127.0.0.1       bacardi

/etc/hostname:
bacardi

output of ifconfig while chrooted:
eth0      Link encap:Ethernet  HWaddr 00:0C:76:DF:3A:6B
          inet addr:192.168.1.100  Bcast:192.168.1.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:23563 errors:0 dropped:0 overruns:0 frame:0
          TX packets:16683 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0
          RX bytes:28510657 (27.1 MiB)  TX bytes:1842351 (1.7 MiB)

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:14 errors:0 dropped:0 overruns:0 frame:0
          TX packets:14 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0
          RX bytes:700 (700.0 b)  TX bytes:700 (700.0 b)

Thanks.

---

### Post by SnoZ on 2005-01-11
sorry but i'm not able to help you in that, that seems way advanced for my "skills"  8-[

---

