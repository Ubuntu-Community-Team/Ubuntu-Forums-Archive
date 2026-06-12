---
title: "Ubuntu 9.04, Intel 4965 and 802.11n"
date: 2009-04-27
forum: Hardware
---

### Post by pcooley on 2009-04-27
I'll admit that I am a novice in terms of wireless configuration and linux distributions.

Although I've read many a thread, it is still unclear to me the support of 802.11n (draft-n) in Ubuntu for the Intel 4965 card.

Laptop: IBM Thinkpad T61
NIC: 03:00.0 Network controller: Intel Corporation PRO/Wireless 4965 AG or AGN [Kedron] Network Connection (rev 61)
Router: D-Link DIR-655 - Hardware version: A4, Firmware version: 1.21
uname -a:Linux pcc-t61-ubuntu 2.6.28-11-generic #42-Ubuntu SMP Fri Apr 17 01:58:03 UTC 2009 x86_64 GNU/Linux
Ubuntu version: 9.04 - Jaunty Jackalope

The below is the results of a iwlist scan and a iwconfig (slightly edited for brevity).

There is 'conflicting' information in that it appears to be connected at 60Mb/s (higher than 802.11g rates) but not near the 130 Mb/s expected.  It appears to make little difference whether I am 4 ft vs. 20 ft away.

802.11n would be handy because I tend to move video to the laptop (stream/download on the local LAN - MythTV).  In Vista 64bit my observed speeds with the same interface were indeed higher -- if I'd be willing to wait 5 - 10 minutes for the OS to boot :-).

Can anyone steer me in the right direction?

```

user@thinkpad-t61-ubuntu:~$ iwlist scan
wlan0     Scan completed :
          Cell 01 - Address: 00:21:**:**:**:**
                    ESSID:"*****************"
                    Mode:Master
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=100/100  Signal level:-41 dBm  Noise level=-94 dBm
[snip]
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s


```

```

user@thinkpad-t61-ubuntu:~$ iwconfig


wlan0     IEEE 802.11abgn  ESSID:"***********************"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:21:**:**:**:**   
          Bit Rate=60 Mb/s   Tx-Power=14 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality=100/100  Signal level:-46 dBm  Noise level=-90 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


```

---

### Post by zyrorl on 2009-05-01
I've found that im unable to get 802.11n speeds though the card itself works fine... it never ever syncs above 54mbps.. yes.. i do have an 802.11n router.. in vista i do get far higher sync speeds.

---

### Post by pcooley on 2009-05-02
Zyrorl,

Agreed, the wireless card works just not at 802.11n draft speeds. 

I didn't say above that the router I am using (D-Link DIR-655) is a draft 2.0 802.11n compliant device.

---

### Post by Gausian on 2009-05-02
Same here.  60Mb/s is what i see

---

### Post by jmurch on 2009-06-11
This is exactly whats happening to me as well.  I've noticed that this or similar problems on Ubuntu with this card are posted in many many forums but no one has any answers.

Jeff

---

### Post by clarksnyder on 2009-09-26
[FONT=Verdana][SIZE=2]I have the same[/SIZE][/FONT][SIZE=2] problem with an Intel 5100 AGN and a D-Link DIR-655 router...my only solution has been to set the router to G only traffic, otherwise the wireless N connection is just too unstable...just curious if others have found a solution or better work around.
[/SIZE]

---

### Post by japher on 2009-11-15
Has anyone found a solution to this yet?

I have an Intel WiFi Link 5100 Wireless nic and Netgear DG834N router, and the speed shows as 60Mb/s. iwlist scan shows the following speeds:
```

Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
          24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
          12 Mb/s; 48 Mb/s

```I'm using Jaunty. Very disappointing. Just bought a new N class router and find that no-one seems to be able to get N speeds on Ubuntu :(

---

### Post by maphilli14 on 2009-11-15
Doesn't even show on my Lenovo T61 running Karmic:

```

wlan0     IEEE 802.11abgn  ESSID:"BLUE"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:23:5E:B0:72:60   
          Bit Rate=0 kb/s   Tx-Power=14 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=59/70  Signal level=-51 dBm  Noise level=-92 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

I've not run a speed test of any sort yet to see what I think it might be.

PS the WLAN is Cisco Airespace 1252's on a WLC44xx running 5.x code that fully supports the latest 802.11n  I'll have to reboot on this machine into the Win7 partition and see what it does!  SOMEONE REMIND ME TO DO THAT and I DON'T WANT TO!  :P

---

### Post by japher on 2009-11-16
Maybe this thread should be moved to the Networking & Wireless forum? It belongs there IMO.

pcooley: If you're still following this, are you able to move the thread? (I expect we probably need a mod)

---

### Post by BartBlackMagic on 2010-02-16
Is there still no solution for this problem?
In Win7 I can connect a Belkin N router using my 4965agn with 130Mbit speeds, in Kubuntu 9.10 I never get higher than 54Mbit..

---

### Post by SaintDanBert on 2010-04-09
I don't know if I have this exact problem because I cannot keep the wireless link running long enough.

When streaming internet radio, every couple of minutes the flash-let starts "buffering" and "connecting" and eventually wakes up again.

When browsing the web, next-page attempts fail routinely and I get the dlink default search-for-address page.

I run [highlight]sntop[/highlight] and it reports that the DIR-655 connection is DOWN. ('sntop' uses fping to a configured IP address)

I run [highlight]wavmon[/highlight] and the radio aspects of my wireless always appears to run fine.  (My workstations have Intel 4965 AGN cards.)

Any ideas,
~~~ 0;-Dan

---

