---
title: "Airodump-ng Problems"
date: 2008-08-06
forum: General Help
---

### Post by Lucroth on 2008-08-06
Okay, so I've messed around with Backtrack 3 a bit for fun as I have an interest in computer security but like Ubuntu so rather than using the Backtrack livecd I've started installing the tools I like from it on my Ubuntu laptop. 
Having a bit of a problem getting airodump-ng to work though. I know that my wireless usb dongle has the ability to do everything needed to crack wep keys and things as I've done it in backtrack just can't seem to get airodump to work in Ubuntu so far.

Turning on monitor mode...
```

computer@computer-laptop:~$ sudo airmon-ng


Interface	Chipset		Driver

eth1		ZyDAS		zd1211rw

computer@computer-laptop:~$ sudo airmon-ng start eth1


Interface	Chipset		Driver

eth1		ZyDAS		zd1211rw (monitor mode enabled)

computer@computer-laptop:~$ sudo airmon-ng


Interface	Chipset		Driver

eth1		ZyDAS		zd1211rw


```
Not sure why monitor mode immediately appears to be off when I check it right after.. that could be problem but not sure..

```

computer@computer-laptop:~$ sudo iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11b/g  ESSID:off/any  Nickname:"zd1211"
          Mode:Monitor  Frequency:2.432 GHz  Access Point: Invalid   
          Bit Rate=1 Mb/s   
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```
iwconfig shows monitor mode though.

On one forum I read someone suggested trying
```

ifconfig eth1 up

```
for a similar problem but that doesn't seem to work either.
```

 CH 11 ][ Elapsed: 12 s ][ 2008-08-06 14:51                                         
                                                                                            
 BSSID              PWR  Beacons    #Data, #/s  CH  MB  ENC  CIPHER AUTH ESSID
                                                                                            
                                                                                            
 BSSID              STATION            PWR   Rate  Lost  Packets  Probes  

```
It will just go on and on receiving nothing, I have ran it for aslong as 5 minutes and got nothing. I am in range of my wireless router. Any ideas?

---

### Post by MyR on 2008-08-06
make sure network manager isn't interfering. right click on the icon and uncheck enable wireless.

peace

---

### Post by pytheas22 on 2008-08-06
A way to test whether monitor mode is really working or not is to disconnect from your router, then run tcpdump:
```

sudo tcpdump -i eth1
```

Wait a few minutes.  If it picks up anything, then monitor mode must be working; otherwise there is some trouble.

You could also try running Wireshark to see if you can pick up traffic that way:
```

sudo apt-get install wireshark
```

If you can't get monitor mode to work, have you checked the aircrack documentation for [installing drivers]("http://www.aircrack-ng.org/doku.php?id=install_drivers&DokuWiki=887374f3f56e302e5a4559ece50f69bd")?  Backtrack comes with everything pre-configured to work properly, but a lot of the wireless drivers that ship with Ubuntu don't support monitor mode; you have to recompile them yourself to add that support.

---

### Post by Lucroth on 2008-08-06
Okay I've turned off wireless in network manager. It was on, but that apparently wasn't the problem or at least not the only problem.

Output from tcpdump:
```

computer@computer-laptop:~$ sudo tcpdump -i eth1
tcpdump: WARNING: eth1: no IPv4 address assigned
tcpdump: verbose output suppressed, use -v or -vv for full protocol decode
listening on eth1, link-type IEEE802_11_RADIO (802.11 plus BSD radio information header), capture size 96 bytes

0 packets captured
0 packets received by filter
0 packets dropped by kernel

```

Doesn't seem to pick up anything. So maybe monitor mode isn't working and I'll try to reinstall the drivers to see if that gets it working.

---

### Post by MyR on 2008-08-06
check the aircrack-ng website to see if your drivers need patched?

peace

---

### Post by sapto on 2010-08-05
Can you help me?Can I run airo dump on win 7?I have Atheros ar5b91 in lap top...is that compatibility?Thanks

---

### Post by MyR on 2010-08-05
> **sapto said:**
> can you help me?can i run airo dump on win 7?i have atheros ar5b91 in lap top...is that compatibility?thanks

no

---

