---
title: "Need help with wireles"
date: 2005-05-16
forum: Hardware &amp; Laptops
---

### Post by CAPTAIN RON FL on 2005-05-16
I need help setting up my notebook wireless connection.

I have a Toshiba Satellite M35X-S109.

It has ethernet built in. I was able to use the Network settings to get it to work. It is configured as eth0.

However I can not seem to be able to get the wireless to work. I tried to set up the wireless first. In fact I tried several times over several days. As a last resort I set up my ethernet connection so I could at least get on the internet. 

I am using a Netgear WG511. The "good" card. At the top of the bar on the far right side it shows two screens and a bar next to them. When I click on them it says that I have 100% for my Network Connection:eth1. I think that means something is working???

I am using a Belkin 54g wirless router going to a Motorola broadband.

This is what I get when I run ifconfig:

   TX packets:2210 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:4172852 (3.9 MiB)  TX bytes:283489 (276.8 KiB)
          Interrupt:21 Base address:0x3000

eth1      Link encap:Ethernet  HWaddr 02:10:91:79:78:15
          inet6 addr: fe80::10:91ff:fe79:7815/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:185 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:55034 (53.7 KiB)
          Interrupt:16

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:22202 errors:0 dropped:0 overruns:0 frame:0
          TX packets:22202 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:2023126 (1.9 MiB)  TX bytes:2023126 (1.9 MiB)


Some one please help me get this set up. ](*,) 

Thanks, Ron

---

### Post by Staesys on 2005-05-16
From what I've seen online, that particular wireless card has some issues with Linux.

[http://prism54.org/supported_cards.php](http://prism54.org/supported_cards.php)

From what you posted above, it looks like your card is not getting an ip address. Are you running WEP? If so, try disabling WEP on your router and see if it'll connect and get and IP address then.

Try **dhclient eth1** and see what happens. Also, what does **iwlist eth1** show? Can you see any access points?

Perhaps this site [http://linux.toshiba-dme.co.jp/linux/index.htm](http://linux.toshiba-dme.co.jp/linux/index.htm)  will be of some help also.

-Paul

---

### Post by CAPTAIN RON FL on 2005-05-16
This what I get:

p@ubuntu:~$ dhclient eth1
Internet Systems Consortium DHCP Client V3.0.1
Copyright 2004 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

sit0: unknown hardware address type 776
can't create /var/lib/dhcp3/dhclient.leases: Permission denied
SIOCSIFADDR: Permission denied
SIOCSIFFLAGS: Permission denied
SIOCSIFFLAGS: Permission denied
sit0: unknown hardware address type 776
Open a socket for LPF: Operation not permitted
p@ubuntu:~$ iwlist eth1
iwlist: unknown command `eth1'

I am not using WEP. It seems that DHCP is not working. At least for some reason I am not able to get an IP address.

OK after looking through the search. I did this:

p@ubuntu:~$ sudo dhclient eth1
Password:
Internet Systems Consortium DHCP Client V3.0.1
Copyright 2004 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

sit0: unknown hardware address type 776
sit0: unknown hardware address type 776
Listening on LPF/eth1/02:10:91:f6:3f:5e
Sending on   LPF/eth1/02:10:91:f6:3f:5e
Sending on   Socket/fallback
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 12
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 15
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 5
No DHCPOFFERS received.
No working leases in persistent database - sleeping.


It seems to not do a complete search. I know I am using channel 11 but it does not show up.

Thanks, Ron

---

### Post by ddocta on 2005-05-17
Have you tried manually entering your essid and key manually using iwconfig, then doing ifdown and ifup on the device.  I have had a reidiculous amount of wireless card  issues with other distros.  I know that worked for me a couple of times.

---

### Post by CAPTAIN RON FL on 2005-05-17
When I run iwconfig, this is what I get. 

p@ubuntu:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11b/g  Mode:Managed  Frequency:2.457 GHz
          Access Point: 00:00:00:00:00:00   Bit Rate:0 kb/s   Tx-Power=31 dBm
          Sensitivity=20/200
          Retry min limit:8   RTS thr:2347 B   Fragment thr:2346 B
          Link Quality:57  Signal level:0  Noise level:64
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.

p@ubuntu:~$ ifdown
ifdown: Use --help for help
p@ubuntu:~$ ifup
ifup: Use --help for help


    I tried manually entering it and I do not use a key.  Also I notice that eth0 is my default and it will not let me change it.  Just like  I am stuck with just one screen resoluction and can't change that either. I am ok with that for now, but must have wireless.

Using search, I found other people are having the same problems with dhcp.
Maybe it is a bug. But then I found other people who have similar problems able to fix it. So there must be a work around of some kind. 

Also I was wondering if I need to deactivate eth0 to get eth1 to work. Should I go back and deactivate both and start over each time I try to get my wireless working. I know there is some type of conflick going on. When I boot up without the ethernet cord hook up I can not get it to work with out rebooting.

The only reason I am using eth1 as my wireless is that it was filled in automaticlly. I read somewhere that wireless likes to be eth0 but this was already assign to my built in ethernet.

Anyone have any more sugestions? I would be willing to buy a new wireless card but that does not seem to be the problem. This is the the first time I really have tried to get it working as it seem too complicated in the beginning. But now I am desperate.   I know there are people out there who have their's working with little or no problems. There must be a solution. ](*,) 

I really need this to work and I really want to use Ubuntu. 
I know that I could use Linspire but I really like Ubuntu... it's not the money. Also they have problems Dual booting anyway and I need XP for a couple of programs. 

Send out the dogs... I am lost. :???:


Aloha, Ron

---

### Post by spd106 on 2005-05-17
Hi, can you see the ap?
Use ```
$sudo iwlist eth1 scan
```Also you need to specify which adapter when you do ifup/down. ie ```
$sudo ifup eth1
```

---

### Post by CAPTAIN RON FL on 2005-05-17
Did all that and still nothing. ](*,) 
Now nothing works. My ethernet is no longer working and I have to use another computer.
HELP!!!

OK just got ethernet to work again, but still no wireless. ](*,) 

aloha, Ron

---

### Post by FrozenBubble on 2005-05-18
There is an excellent thread detaling how to get a wireless card working.  
I followed the tutorial and got it to work in about an hour with the exception that when I reboot it doesnt load the ndiswrapper module.

[http://ubuntuforums.org/showthread.php?t=31926&highlight=wireless](http://ubuntuforums.org/showthread.php?t=31926&highlight=wireless)

Could someone please tell me how to make modprobe load ndiswrapper during boot?

---

### Post by Staesys on 2005-05-18
Add something like this to your /etc/network/interfaces file, substituting your info of course.

```
iface wlan0 inet dhcp
wireless-essid home
wireless-key XXXXXXXXXXXXXXXXXXXXXXX

auto wlan0
``` 

That should do it.

---

