---
title: "snd-ida-intel softmodem (ATI SB450 HDA Audio) and SLMODEMD SOLUTION"
date: 2008-09-10
forum: Hardware
---

### Post by yammosk on 2008-09-10
Hi, 
I stumbled across quite a few people who had troubles initializing their ATI SB450 HDA Audio softmodem with slmodem in the forum archives. I found a solution and it seems to me that it hasn't been posted yet. If it has, my apologies and may the forum gods go easy on me. :)

My modem is detected as following by scanmodem:

```
Modem or host audio card candidates have firmware information:

 PCI slot	PCI ID		SubsystemID	Name
 ----------	---------	---------	--------------
 00:14.2	1002:437b	1462:0369	Audio device: ATI Technologies Inc SB450 HDA Audio 
```

I got it working by doing the following: 

[LIST]
[*]Use scanmodem to confirm your audio chip
[*]Install the newest slmodemd (SLMODEMD.gcc4.2.tar.gz) from [http://linmodems.technion.ac.il/packages/smartlink/]("http://linmodems.technion.ac.il/packages/smartlink/") This *might* work with the slmodemd packaged with (K)Ubuntu, but chances are slim. In my case, the slmodemd-version from the ubuntu repositories was unstable; I couldn't hold an internet connection for more than 2 minutes. 
[*]Untar the archive, browse to it, open a text editor there and [*]Install slmodemd with the following command: 
```
sudo ./setup
```
[/LIST]

Then initialize slmodemd with the following command: 
```
sudo slmodemd --alsa -c YOUR_COUNTRY modem:0
```

The command recommended by Scanmodem (sudo slmodemd --alsa -c YOUR_COUNTRY hw:0,6) did NOT work for me. 

Anyway, I hope this helps those that still seek to make their softmodem work. Good luck. :)

Greetz 

Yammosk

---

