---
title: "Linksys WPC54G install/config on Ubuntu 5 and Acer Travelmate 341T"
date: 2005-08-05
forum: Hardware &amp; Laptops
---

### Post by Seamus on 2005-08-05
HI All,

i know there has been a lot of threads on getting wireless card configured, and I am sure I have read ALL of them and I am so close to getting this sorted I am sure.

I have inserted the PCMCIA card in and installed the ndiswrapper drivers:

sam@acer:~$ sudo ndiswrapper -l
Installed ndis drivers:
lstinds driver present, hardware present

Furthermore, the ifconfig displays the card:


wlan0     Link encap:Ethernet  HWaddr 00:14:BF:03:9D:EC
          inet6 addr: fe80::214:bfff:fe03:9dec/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:22 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:6192 (6.0 KiB)
          Interrupt:9

Now I can also see it through the Gnome network config tool as well, and the device manager also recognises it (although interestingly for the status of the card it simply says "status".)

Despite all of the above, the powerlight on the PCMCIA card is not on, but I can seemingly do scans ok:


sam@acer:~$ cardctl status
Socket 0:
  3.3V CardBus card
  function 0: [ready]


sam@acer:~$ sudo iwlist wlan0 scan
wlan0     No scan results

That would indicate that the card is being accessed - yes, by PCMCIA service is running:

 sudo /etc/init.d/pcmcia restart
 * Shutting down PCMCIA services...                                      [ ok ]
 * Starting PCMCIA services...                                           [ ok ]

When I set the config of the card to DHCP it seems to hang for quite a while with that - is that a possible problem?

Any help greatly appreciated!!

---

### Post by nige on 2005-08-20
Try using different drivers. [Try These, ](http://theweirdone.iwarp.com/LinksysDrivers.rar)  I know that work on v1.2 of the WPC54G, 

I am using the wpc54g + wrt54g flawlessly with the broadcom drivers.
Make sure that you use the wpa_supplicant if you want to use the WPA / WEP. I never was able to get the WEP to work whilest using teh gnome networking tools.

Check your card using the lspci.
That will tell you the chipset the card is using.

---

