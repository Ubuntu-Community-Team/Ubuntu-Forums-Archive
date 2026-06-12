---
title: "Ethernet modem problem"
date: 2011-12-30
forum: Hardware
---

### Post by NilPointer on 2011-12-30
Hello, everyone. I'm having problems with my adsl modem. It seems to be malfunctioning, but I want to be sure it's modem fault before buying a new one.

1) Sometimes it's working properly (ranging from few seconds to several hours), then suddenly something "happens". After that, neither external, nor local resources are accessible. That includes modem's control panel at 192.168.1.1. Modem's LEDs show some "activity" from my machine (flashing), so either my machine or modem sends packets, I guess.

2) Pinging 192.168.1.1 in that state results in either silent packetloss, or Destination Host Unreachable:

```
From 192.168.1.X icmp_seq=1295 Destination Host Unreachable
From 192.168.1.X icmp_seq=1298 Destination Host Unreachable

```

So, i guess packets 1296 and 1297 were just lost, while others can't find route to host.

3) I tried to connect via wlan0 instead of eth0 (which is connected to this modem, too) and couldn't access 192.168.1.1 either (pinging says Destination Net Unreachable). This should rule out both eth0 NIC and cable fail, right?

4) Wireshark shows only outgoing ARP traffic (asking who has 192.168.1.1), modem doesn't respond to ARP in any way. Also, for some reason Wiresharks shows IP for eth0 as IPv6.

Well, is there a chance of improperly configured interface or firewall, or modem is done for?

Sometimes, rebooting modem helps and it works for some time again.

---

### Post by Paddy Landau on 2011-12-30
> **NilPointer said:**
> 3) I tried to connect via wlan0 instead of eth0 (which is connected to this modem, too) and couldn't access 192.168.1.1 either (pinging says Destination Net Unreachable). This should rule out both eth0 NIC and cable fail, right?
Not necessarily; it could be that the modem or your computer is not correctly configured for wireless.

Rebooting your modem fixes the problem for a while. What about rebooting your computer -- does that fix the problem for a while? If not, it could be either your modem or your ISP. It would be worth speaking to your ISP in case their diagnostics show some problem on your line.

BTW, I'm presuming that your modem and router are in a single box; is that correct?

---

### Post by NilPointer on 2011-12-30
> **Paddy Landau said:**
> Not necessarily; it could be that the modem or your computer is not correctly configured for wireless.

Rebooting your modem fixes the problem for a while. What about rebooting your computer -- does that fix the problem for a while? If not, it could be either your modem or your ISP. It would be worth speaking to your ISP in case their diagnostics show some problem on your line.

BTW, I'm presuming that your modem and router are in a single box; is that correct?

Well, wireless worked previously (and modem was accessible from it).

There's two chains:

DSL -> Modem/LAN Router -> eth0 on my machine
            |
            V
       Wireless Router -> wlan0 on my machine

Rebooting computer doesn't help at all. I don't think it's ISP problem either, since modem's admin panel should be accessible when there's no internet connection.

Yes, modem in question is also a lan router.

Also, quite interesting results I've got with zenmap scan of range 10.0.0.* (while both eth0 and wlan0 were active). It found my eth0 IP active, so I guess "LAN router" part of modem is still working, yet it couldn't find 192.168.1.1. Perhaps, some servers on modem crashed?

---

### Post by Paddy Landau on 2011-12-30
You have two routers? You have to ensure that they have different IP bases (e.g. 192.168.1.* and 192.168.2.*) to prevent conflicts. Have you done so?

You showed your wireless router connected directly to the DSL; was that meant to show it connected to the moden?

---

### Post by NilPointer on 2011-12-30
It's automatically changes IP base on startup if it detects that 192.168.1.* already used, so it has 10.0.0.* IP range.

Hm, forum engine seems to strip leading spaces in each line... Yes, i meant to show it's connected to modem.

---

### Post by Paddy Landau on 2011-12-30
> **NilPointer said:**
> Hm, forum engine seems to strip leading spaces in each line... Yes, i meant to show it's connected to modem.
OK. To retain spacing, use [FONT=Fixedsys][noparse]```
[/noparse][/FONT] and [FONT=Fixedsys][noparse]
```[/noparse][/FONT] around the section (or highlight the section and press the "#" button on the toolbar). It will look like this when you post (presuming I have correctly understood you):
```
DSL -> Modem/LAN Router -> eth0 on my machine
       |
       V
       Wireless Router -> wlan0 on my machine
```Well, I would suspect that your diagnosis is correct. Perhaps it's time to replace your current set-up with a single wireless router-modem for your ADSL.

If you have Windows, it may be useful to boot into Windows to find out whether or not you have the same problems with both the wired and wireless routers.

---

### Post by NilPointer on 2011-12-30
Well, there was another problem I didn't told about (which was solved yesterday)... My logs (syslog, kern.log, messages) grown up to 21.2 GB each, filled with complaints about arriving oversized packets to eth0. Even that they stopped now, I was told, that they shouldn't have been arrived in first place and either NIC or modem are malfunctioning. Summed with this problem, it seems that it was modem's fault, after all. Paddy Landau, thanks for your help!

Windows also won't work with modem. It couldn't get DHCP IP from it. Also, not a single incoming packet from modem.

---

### Post by Paddy Landau on 2011-12-30
Well, I'm not an expert on this stuff, so I really haven't helped much at all. But it looks like you have found your culprit. Good luck in solving it!

---

### Post by NilPointer on 2011-12-31
Today I've opened modem. There was one blown whistling capacitor (I had feeling I'll find something like that inside). So, it's going to trash. I've bought replacement for faulty modem. Now problem is really solved.

---

### Post by Paddy Landau on 2011-12-31
> **NilPointer said:**
> ... one blown whistling capacitor
LOL - as I know nothing about capacitors, I can only imagine what it means to blow a whistling capacitor! :-\"

I'm glad you found the problem.

---

