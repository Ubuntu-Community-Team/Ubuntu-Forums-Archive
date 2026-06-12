---
title: "Compaq Laptop wireless adapter not working"
date: 2012-01-29
forum: Hardware
---

### Post by pgroves95 on 2012-01-29
I just got a hand-me-down Compaq Presario CQ50-215NR from my dad that was running Vista very sluggishly. I formatted the Hard Drive and installed Ubuntu 11.10. This is my first time using a Linux OS and am so far pleased with the new OS. However, my current wireless network adapter (Atheros AR928X) is incompatible with Linux. I have exhausted my own efforts to try and resolve this issue (I downloaded a Windows XP driver and tried to run it using ndisgtk), and was wondering what my best options are. I'm considering just buying a new wireless card that is Linux-Compatible (could use help in that selection process), or simply buying a USB-adapter. If there is a different distro that is compatible with my adapter, I'm willing to install that, as I haven't personalized anything yet.

NOTE: I am a complete Linux newb with limited vocabulary and no coding knowledge, so please use cave-man speak and reference me to GUI programs.

---

### Post by wolfen69 on 2012-01-29
Did you check *Additional Drivers* for the wireless card? You will need the computer to be physically plugged into a router to do this.

---

### Post by pgroves95 on 2012-01-29
> **wolfen69 said:**
> Did you check *Additional Drivers* for the wireless card? You will need the computer to be physically plugged into a router to do this.

Yes I've also tried this and only the NVidia graphics card appears in the list.

---

### Post by wolfen69 on 2012-01-29
[This]("http://askubuntu.com/questions/65779/how-do-i-get-an-atheros-ar9285-wireless-card-working") person had the same problem and solved it.

Btw, you will need to do:
```
gksudo gedit /etc/modprobe.d/blacklist.conf
```
and add *blacklist acer_wmi* to the bottom of the page. Reboot.

---

### Post by pgroves95 on 2012-01-29
> [QUOTE][QUOTE][QUOTE][/QUOTE][/QUOTE][/QUOTE]Thanks! However, there is a discrepancy, as my rfkill list shows my wireless LAN's to be hard blocked.

```

*-network               
       description: Ethernet interface
       product: MCP77 Ethernet
       vendor: nVidia Corporation
       physical id: a
       bus info: pci@0000:00:0a.0
       logical name: eth0
       version: a2
       serial: 00:1d:72:6b:99:b7
       size: 100Mbit/s
       capacity: 100Mbit/s
       width: 32 bits
       clock: 66MHz
       capabilities: pm msi ht bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=forcedeth driverversion=0.64 duplex=full ip=192.168.2.2 latency=0 link=yes maxlatency=20 mingnt=1 multicast=yes port=MII speed=100Mbit/s
       resources: irq:41 memory:c0009000-c0009fff ioport:30f8(size=8) memory:c0007c00-c0007cff memory:c0007800-c000780f
  *-network DISABLED
       description: Wireless interface
       product: AR928X Wireless Network Adapter (PCI-Express)
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:07:00.0
       logical name: wlan0
       version: 01
       serial: 00:22:69:38:f5:71
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ath9k driverversion=3.0.0-12-generic firmware=N/A latency=0 link=no multicast=yes wireless=IEEE 802.11abgn
       resources: irq:23 memory:c2000000-c200ffff

rfkill list

0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: yes
1: hp-wifi: Wireless LAN
	Soft blocked: no
	Hard blocked: yes
```

 Will blacklisting them still do the trick?

---

### Post by wolfen69 on 2012-01-29
It won't hurt to try. It worked for somebody else.

---

### Post by pgroves95 on 2012-01-29
Didn't help. Now everything on my rfkill list is both hard blocked and soft blocked ```
rfkill list
0: phy0: Wireless LAN
	Soft blocked: yes
	Hard blocked: yes
1: hp-wifi: Wireless LAN
	Soft blocked: yes
	Hard blocked: yes
```

---

### Post by ahallubuntu on 2012-01-29
Unfortunately, in cases like this you just have to google for solutions for 11.10 that people have tried with your Atheros card and with trial and error find one that works.

If you had a Dell, Acer, or Toshiba laptop, I'd tell you to invest about $15 in an Intel internal wireless card and be done with it - Intel cards are well supported in Linux.  Unfortunately, HP (and Lenovo) use something nasty called Whitelisting to block the use of unapproved internal wireless cards - if the BIOS detects one that's "unapproved" for that laptop, it will simply refuse to POST and you can't even boot an operating system.  There are some advanced ways to hack the BIOS and disable whitelisting, but if you mess something up you could brick the laptop completely, so I don't recommend it.

A USB mini-dongle wireless adapter may work.  I've bought a few of them for various projects off eBay for about $6 each (from Asia so wait a few weeks).  They work OK but not as well as an internal laptop WiFi card.  Kind of a pain not to use your internal card; I'm SURE you could get it to work with some trial and error since others have apparently, but it looks like a bit of work.  Sorry!  Ubuntu is great - stick with it, keep trying...

---

### Post by pgroves95 on 2012-01-31
Thanks! I'm quickly learning the linux mindset where perseverance is concerned. It's no rush regardless; I have an ethernet cable hooked up that (fortunately) works fine, even if it limits mobility.

---

