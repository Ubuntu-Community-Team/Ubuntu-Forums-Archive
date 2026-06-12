---
title: "cannot configurate wlan: ipw2200 HOWTO made it worse"
date: 2005-05-09
forum: Hardware &amp; Laptops
---

### Post by pau on 2005-05-09
Hi,

I have a laptop with a built-in wlan intel 2200 and I followed this howto:

[http://www.ubuntuforums.org/showthread.php?t=26623](http://www.ubuntuforums.org/showthread.php?t=26623)

Everything was fine and without errors. The point is that now iwconfig doesn't find my eth1 anymore! before I installed the drivers and so on it was on the list of the network pannel applet and  I could look at its propierties... Now it's gone.

What is the problem? I deinstalled wpasupplicant but this didn't help (btw I don't really know what is this for)

---

### Post by snop on 2005-05-09
Hi Pau,

Is ipw2200 module loaded ? You can check it using "lsmod | grep ipw2200" from a console. If the module is loaded you should see something like this:
```

snop@portatil:~ $ lsmod | grep ipw2200
ipw2200                91528  0
firmware_class          9984  1 ipw2200
ieee80211              24804  1 ipw2200
ieee80211_crypt         5736  3 ieee80211_crypt_wep,ipw2200,ieee80211

```

Also, are you currently running version 1.0.3 or 0.19 (the default and buggy Hoary ipw2200 driver) ? Check it using "dmesg | grep ipw2200". You should see something like this:

```
snop@portatil:~ $ dmesg | grep ipw2200
ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 1.0.3
ipw2200: Copyright(c) 2003-2004 Intel Corporation
ipw2200: Detected Intel PRO/Wireless 2200BG Network Connection

```

SnOp

PD: I'm gonna try to package the newest ipw2200 driver to overwrite the buggy one supplied with Hoary. This may solve other bugs such as connection drops (see: [http://ubuntuforums.org/showthread.php?t=21056&page=1&pp=10](http://ubuntuforums.org/showthread.php?t=21056&page=1&pp=10))

PD2: BTW, Pau it's a common name where I live and means "peace" ;) Are you Catalan perhaps ?

---

### Post by pau on 2005-05-09
Hola!

Si el meu ordinador es diu "andròmina", jo em dic pau i tinc ficat el gnome en Català, podem donar per fet que, encara que no sóc Català, parle Català  \\:D/ 

----

I will post the answer in English-Pitinglish anyway because it may be of help to other people too...

(1) lsmod | grep ipw2200  yields nothing in my laptop

(2) I installed 1.0.3, but look at this:

andromina| dmesg | grep ipw2200                                                                                          

ipw2200: disagrees about version of symbol ieee80211_wx_set_encode
ipw2200: Unknown symbol ieee80211_wx_set_encode
ipw2200: disagrees about version of symbol ieee80211_wx_get_encode
ipw2200: Unknown symbol ieee80211_wx_get_encode
ipw2200: disagrees about version of symbol ieee80211_wx_get_scan
ipw2200: Unknown symbol ieee80211_wx_get_scan
ipw2200: disagrees about version of symbol ieee80211_rx
ipw2200: Unknown symbol ieee80211_rx
ipw2200: disagrees about version of symbol ieee80211_rx_mgt
ipw2200: Unknown symbol ieee80211_rx_mgt

Any idea? I didn't get any error during compilation...  ](*,) 


Thanks in advance...

Pau

PS: Where are you from, snop?

---

### Post by flipy on 2005-05-09
[QUOTE=pau]Hola!

Si el meu ordinador es diu "andròmina", jo em dic pau i tinc ficat el gnome en Català, podem donar per fet que, encara que no sóc Català, parle Català  \\:D/ 

----

I will post the answer in English-Pitinglish anyway because it may be of help to other people too...

(1) lsmod | grep ipw2200  yields nothing in my laptop

(2) I installed 1.0.3, but look at this:

andromina| dmesg | grep ipw2200                                                                                          

ipw2200: disagrees about version of symbol ieee80211_wx_set_encode
ipw2200: Unknown symbol ieee80211_wx_set_encode
ipw2200: disagrees about version of symbol ieee80211_wx_get_encode
ipw2200: Unknown symbol ieee80211_wx_get_encode
ipw2200: disagrees about version of symbol ieee80211_wx_get_scan
ipw2200: Unknown symbol ieee80211_wx_get_scan
ipw2200: disagrees about version of symbol ieee80211_rx
ipw2200: Unknown symbol ieee80211_rx
ipw2200: disagrees about version of symbol ieee80211_rx_mgt
ipw2200: Unknown symbol ieee80211_rx_mgt

Any idea? I didn't get any error during compilation...  ](*,) 


Thanks in advance...

Pau

PS: Where are you from, snop?[/QUOTE]
 Potser s'hauria de fer un fòrum català...
------
i've got some troubles with a laptot using that drivers. I know this must sound silly, but after compiling/making/trying a lot of things I've ended using ndiswrapper... You can use it as a temporal solution until you find the correct bug/failure

---

### Post by pau on 2005-05-09
I com es fa aixó?

what are the differences between ndiswrapper and ipw2200? why should it be worse?

why temporary? why why? why why why? 

I still don't know what is an essid, key...

I am used to eth0... you plug in, bring it up and that's it...

I have a wlan at home and would like to use... but sometimes i am at a so-called hotspot and I would like how to use my linux box on it (I deleted the window$ partition) 

Could ndiswrapper be the solution?

---

### Post by Gandalf on 2005-05-09
just a quick answer, DON'T USE 1.0.3 use 1.0.0, 1.0.3 is unstable, i tried 1.0.0, 1.0.2 and 1.0.3 only 1.0.0 works

---

### Post by pau on 2005-05-09
You are right... 1.0.0 is working

andromina| iwconfig                                                           ~
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      unassociated  ESSID:off/any
          Mode:Managed  Channel=0  Access Point: 00:00:00:00:00:00
          Bit Rate=0 kb/s   Tx-Power=off
          RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.


And now?

Why is my ESSID not there? I tried to set it up with the applet but it didn't work...

---

### Post by luca_linux on 2005-05-09
As said in the howto the errors you got depend on some older module. Delete all the ipw2200.ko and ieee80211*.ko modules and then install the new version and copy them into the other directory too.

---

### Post by snop on 2005-05-09
[QUOTE=Gandalf]just a quick answer, DON'T USE 1.0.3 use 1.0.0, 1.0.3 is unstable, i tried 1.0.0, 1.0.2 and 1.0.3 only 1.0.0 works[/QUOTE]

Haven't tried other versions than 0.19 (supplied with Hoary) and 1.0.3.

Since I installed 1.0.3 my connection hasn't drop. So for me works like a charm. I'm using an Acer Travelmate 4001Wlmi.

> And now?

Why is my ESSID not there? I tried to set it up with the applet but it didn't work...

The applet didn't work for me as well. You may try this [http://www.bitbuilder.com/wifi_radar/](http://www.bitbuilder.com/wifi_radar/) (you'll probably find it at the repository, can't check it now, sorry).

Also, for driver 1.0.3, check luca_linux tutorial (that's what I followed). Driver paths are a little tricky. Make sure you followed exactly what he says.

BTW luca_linux, perhaps you should mention in your tutorial that instead of copying all the drivers from one location to another you could modify the Makefile:
```
KMISC := /lib/modules/$(KVER)/drivers/net/wireless/
to
KMISC := /lib/modules/$(KVER)/kernel/drivers/net/wireless/
```

Using this then only ipw2200.ko should be moved. But great How-to anyway.

Bonus points: The driver can handle the led driver (it's experimental code, though). In order to do so you must pass "led=1" when "modprobing" the driver. To make it permanent you can create a file named ipw2200 at /etc/modprobe.d and type:

```
echo "options ipw2200 led=1" > /etc/modprobe.d/ipw2200
```

SnOp

PD: We shouldn't write in Catalan in this forum... but I'm glad to see I'm not the only Catalan here ;)

---

### Post by pau on 2005-05-10
Hi, thank you at all of you and especially to Luca, for providing us with such a nice and clear howto
However I cannot connect to wlan yet but I _know_ it's only my fault because everything is working, I think...

Look at this:

```
andromina# iwconfig
lo        no wireless extensions.

sit0      no wireless extensions.

eth0      no wireless extensions.

eth1      unassociated  ESSID:"WLAN"  Nickname:"WLAN"
          Mode:Managed  Channel=255  Access Point: 00:00:00:00:00:00
          Bit Rate=0 kb/s   Tx-Power=20 dBm
          RTS thr:off   Fragment thr:off
          Encryption key: a-long-key   Security mode:open
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```

Why is my security mode open?

```
andromina# iwlist eth1 scan
eth1      Scan completed :
          Cell 01 - Address: 00:03:C9:7D:91:85
                    ESSID:"WLAN"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:11
                    Encryption key:on
                    Bit Rate:54 Mb/s
                    Extra: Rates (Mb/s): 1 2 5.5 6 9 11 12 18 24 36 48 54
                    Signal level=-58 dBm
                    Extra: Last beacon: 0ms ago
          Cell 02 - Address: 00:01:E3:41:E7:59
                    ESSID:"ConnectionPoint"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:11
                    Encryption key:on
                    Bit Rate:54 Mb/s
                    Extra: Rates (Mb/s): 1 2 5.5 6 9 11 12 18 24 36 48 54
                    Signal level=-83 dBm
                    Extra: Last beacon: 45ms ago

```

Cell 2 is the 2nd computer from which we put the MAC number?? 

```
andromina# dhclient eth1
Internet Systems Consortium DHCP Client V3.0.1
Copyright 2004 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/products/DHCP

sit0: unknown hardware address type 776
sit0: unknown hardware address type 776
Listening on LPF/eth1/00:0e:35:6a:43:3c
Sending on   LPF/eth1/00:0e:35:6a:43:3c
Sending on   Socket/fallback
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 14
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 17
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 11
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

```

So... what's going on?

I installed also wifi-radar, but normal users can employ it... 

I followed [http://www.bitbuilder.com/wifi_radar/](http://www.bitbuilder.com/wifi_radar/) ...

I am not sure whether I used the right essid and key... I don't know what's a key and essid however... I guess essid is what iwconfig showed me the first time and the key is something like 372F-D53E-B234-716D-BFE9-4954-54
which was generated by the router when I gave it a password of my choice...
Am I right?
This is like Chinese!!

---

### Post by snop on 2005-05-10
> I am not sure whether I used the right essid and key... I don't know what's a key and essid however... I guess essid is what iwconfig showed me the first time and the key is something like 372F-D53E-B234-716D-BFE9-4954-54
which was generated by the router when I gave it a password of my choice...

It seems that ipw2200 driver is working fine. You "just" need to associate to a wireless network.

The essid is the name of the access point you want to connect to. The key... is the wep encryption key set in the router. You should try to disable wep encryption (this is done in a different way, depends on your router. Check [http://www.adslayuda.com](http://www.adslayuda.com) to see some nice how-to's).

When disabling your wep encryption you should be able to connect to your access point issuing a command like this:
```
sudo iwconfig eth1 essid WLAN
or (depending on what net you intend to connect to)
sudo iwconfig eth1 essid ConnectionPoint
```

Then issuing "iwconfig" you should see that "Access Point" is no longer 00:00:00:00:00:00 but the mac address of your access point of choice. 
This is my iwconfig output:
```
eth1      IEEE 802.11g  ESSID:"PADRONET"
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:80:5A:22:AC:8A
          Bit Rate=54 Mb/s   Tx-Power=20 dBm
          RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=89/100  Signal level=-40 dBm  Noise level=-83 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:46  Invalid misc:0   Missed beacon:0
```

When your unencrypted connection works try to set a wep key in your router. Then you can try to connect to your wireless access point like this:

```
sudo iwconfig eth1 essid WLAN key 1212121212
```

This example uses a 64 bit wep key (the number of bits in your wep key should be chosen through your router's set up gui).

Hope this helps.

Bye

PD: When choosing "Security Mode" you should choose "open" instead of "shared". I had problems using shared mode with ipw2200 and I read somewhere that open mode is more secure. I don't know what are the differences between this modes, though.

---

### Post by pau on 2005-05-10
Hi

thanks for the explanation... 

I followed your advice and switched off wep and selected open but this didn't help when doing an iwconfig eth1 essid lameua

When I type iwconfig I don't get the MAC number, just 00:00: ...

What about dhcp/ IP? The applets are asking me what the IP is... I just know my gateway but no idea what the ip should be. On the other hand, if I choosed dhcp, which are the DNS?

When I installed ubuntu it asked me whether I wanted to configurate eth0 or wlan. I chose eth0 because I knew it would work for sure but maybe I should have let ubuntu configurate wlan...

**what can I do?**

---

### Post by snop on 2005-05-10
[QUOTE=pau]
When I installed ubuntu it asked me whether I wanted to configurate eth0 or wlan. I chose eth0 because I knew it would work for sure but maybe I should have let ubuntu configurate wlan...
**what can I do?**[/QUOTE]

Mmm, I'm not sure. What kind laptop are you using ? There are how-to's specifics for certain models. Some laptops even need "acer hot keys" driver to enable wireless connection even on some non Acer models ([http://www.informatik.hu-berlin.de/~tauber/acerhk/)](http://www.informatik.hu-berlin.de/~tauber/acerhk/)).

> What about dhcp/ IP? 
If your router uses the default configuration you'll better leave your ip configuration to dchp. Otherwise (and to make it plain simple) you could --probably-- try to set your ip to anything like 192.168.1.X (Where X is any number between 2 and 254). 

Bye and good luck.

PD: Take into account that I'm, by no means, an network config expert (I can hardly make my connection work...).

---

### Post by pau on 2005-11-25
Ok, I've got it... the problem was the sequence of things + mac address from router...

[http://www.aei.mpg.de/~pau/amilo_1425_linux.html]("http://www.aei.mpg.de/~pau/amilo_1425_linux.html")

There is a link to an english version, on the top of the screen... Also it is explained how to use it with encryption

Make first sure that your firewall is not enabled

```
ps aux |grep firestarter
```

If you find it, then

```
pkill -15 process_number
```
                                                                                                                                           
Just in case of,

```
ps aux |grep dhcpcd
```      

And you do the same.

Well now you have to be sure the sequence of things you do is THIS one:
                                                                                                                                           
```
ifconfig eth0 down
                                                                                                                                           
ifconfig eth1
                                                                                                                                           
iwconfig eth1 essid "the_name_of_your_essid"
                                                                                                                                           
dhcpcd eth1
```

And that's it! 

One more thing: If you have a mac address filter on your router, be sure to upload the address of **both** devices, eth0 and wlan to it! 

You can find the number like this:

```
iconfig -a
```

The mac address is the number looking like 03:R4:3G:blablabla

---

### Post by pau on 2005-11-25
```
ifconfig eth1 up
```

of course... sorry, the "up" was missing

---

### Post by pau on 2005-11-30
Hi,

there is a better explanation here

[http://www.ubuntuforums.org/showthread.php?t=96998&highlight=pau]("http://www.ubuntuforums.org/showthread.php?t=96998&highlight=pau")

cheers,

Pau

---

### Post by andrew73a on 2008-02-01
OK, 
  I just installed Fedora core 6 onto my laptop. I have a compaq presario v2000 with an Intel(R) Pro/Wireless 2200 802.11BG WLAN.  I really need someone to walk me through how to install the drivers to make my wireless work. I read about 20 "How To" articles... and I can't understand anything. Please help and feel free to e-mail me.  Thank you very much.

---

