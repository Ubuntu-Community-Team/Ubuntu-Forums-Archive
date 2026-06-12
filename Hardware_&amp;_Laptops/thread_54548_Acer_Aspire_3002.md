---
title: "Acer Aspire 3002"
date: 2005-08-05
forum: Hardware &amp; Laptops
---

### Post by elwis on 2005-08-05
I've recently bought myself an Acer and planned to dualboot it. Now I don't know wether I'll put suse or Ubuntu on the 2nd partition, my heart says Ubuntu ;)

I'm totally lost with Linux and wireless, are there any tols for configuring it? And, as far as I understand, trying to get the builtin wireless to work is doomed.. I better buy myself a prism PCMCIA card.. right/wrong??

Me != Hardware

---

### Post by scweble on 2005-10-05
I have an aspire 3002wlmi and it runs fine on breezy.
You can use the sis driver to get 1280x800 and ndiswrapper+windows driver for the wireless card.

---

### Post by Confuse on 2005-10-05
[QUOTE=scweble]I have an aspire 3002wlmi and it runs fine on breezy.
You can use the sis driver to get 1280x800 and ndiswrapper+windows driver for the wireless card.[/QUOTE]

I have the same laptop and ran exceptionally well on breezy and hoary. I'd go with ubuntu, you just need ndiswrapper to get the wireless to work and be sure the wireless button is ON.

scweble, can you give me more info on running 1280x800? The spec say its only 1024x768 I believe. Any info on this would be highly appreciated. Thanks.

EDIT: Nevermind, you have the 15.4 screen, I have the 15" screen. ;[

---

### Post by scweble on 2005-10-08
Do you also have the battery status and hibernating/standby working?
My battery status always says it's plugged in so I never know when it's empty untill it suddenly powers down.
When I hybernate the system and switch it back on the keyboard is'nt working.

---

### Post by skirkpatrick on 2005-10-08
Check out my topic on getting battery & wifi working on this laptop at [http://www.ubuntuforums.org/showthread.php?t=60484](http://www.ubuntuforums.org/showthread.php?t=60484).  I'm helping several others with it as well.

---

### Post by ubuntu_123 on 2005-10-23
Hi everybody, and skirkpatrick.

Thanks skirkpatrick for helping me to setup the wireless, but after a few tries I decide to temporary forget it, I want to do something else.

The video card is getting me a big headache. According to this:

[www.winischhofer.at/linuxsispart1.shtm](www.winischhofer.at/linuxsispart1.shtm)..

Seems there is no way you can do some game programing in linux with this type of video card, I don't know, maybe you guys can come up with something.

The main problem is when I run an OpenGL and FLTK program, the program run through but show the error message after the program run,

"Xlib: extension "XFree86-DRI" missing on display ":0.0"."


Also I run this:
$fglrxinfo
Xlib: extension "XFree86-DRI" missing on display ":0.0".
display: :0.0 screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.2.1)

$glxinfo
name of display: :0.0
Xlib: extension "XFree86-DRI" missing on display ":0.0".
display: :0 screen: 0
direct rendering: No

Some effects can't be showed in the program, for example, like no lighting, no 3D color, but I can see the shape of the object. 

Also, is there any way to reduce the heat of the laptop?

Regards.
yasir.

---

### Post by shahrc on 2006-04-04
My Acer Aspire 3002NCLI does not detect my wireless card on Breezy 5.10. I then tried Dapper 6.06....wallaah..the card detected. However I still can't get it connected.

>  ifconfig eth1
eth1      Link encap:Ethernet  HWaddr 00:0E:9B:B0:37:CA
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:4 Base address:0xc000


[[IMG]http://img417.imageshack.us/img417/3332/networksettings7sj.th.png[/IMG]](http://img417.imageshack.us/my.php?image=networksettings7sj.png)

> 0000:00:0b.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)


> eth1      IEEE 802.11b/g  ESSID:off/any  Nickname:"Broadcom 4318"
          Mode:Managed  Access Point: Invalid   Bit Rate=1 Mb/s
          RTS thr:off   Fragment thr:off


I'm a newbie here and I am also new to linux, I'm just got bored with windows and trying to learn linux now.

Can anybody guide me how to solve this problem?

At last..

I finally made it with Dapper and ndiswrapper...

Thks anyway..

---

