---
title: "wifi on, acer 3610"
date: 2006-02-01
forum: Hardware &amp; Laptops
---

### Post by freddoo on 2006-02-01
hello, 

i search the driver for wifi card broadcom 802/11.g on acer aspire 3610
 please help me

bye

---

### Post by Andrew Shimmin on 2006-02-01
The driver [is here]("https://www.synapsenow.com/synapse/data/7117/documents/AS35-Wireless%20Lan%20b+g%20(Broadcom).zip").

---

### Post by levi on 2006-02-20
I have the same wireless card and just installed ubuntu 5.10 now i would like to install my wireless netword card, can someone please explain how to install this driver?

---

### Post by chaoschannel on 2006-02-20
I'm not sure if this is what your looking for, but as far as I can tell there aren't any linux drivers for the broadcom WIFI, You need to get the windows drivers, then use ndiswrapper to get it working. You should be able to find the windows drivers on Acer's website.

---

### Post by levi on 2006-02-20
Thanx for your reply,

I found the win drivers and installed them with ndiswrapper, still when i give the command "iwconfig" i get:

lo       no wireless exstensions
eth0   no wireless exstensions
sit0    no wireless exstensions

Further "wlan0" seems to be missing.. can you help me out here?

---

### Post by chaoschannel on 2006-02-20
Not sure about that one. I just followed the instructions here: 
[https://wiki.ubuntu.com/WifiDocs/Driver/Ndiswrapper?action=show&redirect=SetupNdiswrapperHowto](https://wiki.ubuntu.com/WifiDocs/Driver/Ndiswrapper?action=show&redirect=SetupNdiswrapperHowto)

[edit]- As an afterthought I also had to use the bcmwl5a.inf file instead of the bcmwl5.inf -[/edit]

---

### Post by levi on 2006-02-20
Well the wlan0 appeared, and i was able to see the different networks in my area. I chose the one wich is mine and entered the needed data as wep key.

But..

I do not have a connection. Although i can see the networks, when i give the command "lspci" it show still not the appropriate information of my wireless card.

---

### Post by chaoschannel on 2006-02-20
I don't think lspci is going to be any use. Mine doesn't list the appropiate information either. Have you set wlan0 as your default in Network Settings? You might also need to set the network monitor Icon on the top panel to wlan0. Not sure though.

---

### Post by levi on 2006-02-20
okey that comforts me then :).. i was looking for this option to get this network monitor icon to the wlan device. But don't know where to do this.

Setting wlan0 as default in network settings doesn't really work, when i set it and press ok, and open again, the default device box is empty..

---

### Post by chaoschannel on 2006-02-20
The network monitor was installed by default on my system. It's on the top right menu. But if it's missing you can right-click the top panel -> Add to Panel -> then scroll down and choose network monitor. 

What does iwconfig say about wlan0?

---

### Post by levi on 2006-02-20
I just started my ubuntu laptop and noticed it holds quite long when loading network interfaces.

I missunderstood you, i do have this network monitor, but it is not possible to set this to wlan0. It is set on "lo" the loopback that ws necessary for sudo to function appropiatly.

wlan0:
IEEE 802.11g ESSID:off/any
Mode managed Frequency 2.412 ghz Accespoint 00:00:00:00:00:00
Bit Rate 54 Mb/s TX power 25dbm
rts thr 2347B Fragment thr: 2346
Power management:off
Link quality100/100 Signal Level: -75dBm Noise Level -256 dBm
Rx invalid nwid:0 Rx invalid crypt:0 Rx invalid frag:0
Tx excessive retries:0 Invalid misc:0 Missed beacon:0

---

### Post by chaoschannel on 2006-02-20
hmm, looks like your network card is detected and running, just not connecting to your network.

You can double check network settings -> Properties, that it has the proper essid and wep key.  And under configuration unless you are configuring it manually, that DHCP is chosen.

You may need to remove all the drivers from ndiswrapper and start fresh. 

Unfortunately I'm not sure what else to do. :-?

---

