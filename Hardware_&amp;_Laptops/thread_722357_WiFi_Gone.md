---
title: "WiFi Gone"
date: 2008-03-12
forum: Hardware &amp; Laptops
---

### Post by linduxed on 2008-03-12
Greetings fellow Ubuntu-users.

I'm being pestered by a WiFi-problem. To put it simply, it doesn't work even though all the settings I know of are correct and coupled with the fact that I hadn't changed anything when it happened.

System specs:
-----------------
Intel 4965AGN PRO/Wireless
2.20 Dual Core
2 Gb Ram

Internet: Socket > Modem > DHCP Router (DLink) > Computers

The long version: Before I start I'd like to point out that I dualboot Windows XP (for gaming, nothing else or I'd be ashamed of myself :-P) and there everything in the laptop always worked/works.
I once tried using Sabayon Linux on my laptop (Zepto ZNote 6625WD) and pretty much abandoned it because no matter what I did and what settings I had, no connection could be made. Either I could only see the APs but never connect, or more often nothing shown at all.
I therefore switched to Ubuntu 7.10 and WiFi worked right away. About two weeks ago I closed my laptop (the lid) and went AFK for a while. When I came back and opened the lid I was greeted by a black screen and flashing LEDs "A-la kernel panic". I did a manual shutdown and Ubuntu got back fine, except for the WiFi.
Here from I tried a lot of things after extensive googling, but what's most important to mention is that WiFi still works in XP and that I noticed some strange things.
In beginning (right after the LEDs and black screen, which I will from now on refer to as the beginning) Windows needed half a minute or so more than the usual 10 seconds to find our WLAN (very strong signal). By this time Ubuntu (and a couple of reboots forward) tended to see APs but not be able to connect to them (worth noting is that I saw notably less APs, only the strongest ones). /var/log/messages showed by this time that RF kill switch was on...which turned out to be untrue as the "cat /sys/bus/pci/drivers/wlan/*/rf_kill" gives "0". What I also noticed was that sometimes WiFi started working if you just waited for a while (usually 15-30 min). During this time you could see the APs but not connect.
Later on however the problem complicated itself even further. WiFi now doesn't work at all at home (you dont see any APs at all with network-manager), but I've noticed that the WiFi works (seemingly) flawlessly at my university (however preserving the trait that less APs are shown, this applies to XP too).

My WiFi is turned on with a switch not a button on this laptop. It's on.
I updated to the latest BIOS, it didn't change anything.
Another fact that suggest something hardware-related is that I get similar results when I try using WiFi with the Live-CD.

If any console output is needed I'll post it.

P.S. For the reference: Sabayon is a great experience on stationary comps. Do try it some time.

---

