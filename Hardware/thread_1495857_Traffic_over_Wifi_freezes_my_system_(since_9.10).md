---
title: "Traffic over Wifi freezes my system (since 9.10)"
date: 2010-05-28
forum: Hardware
---

### Post by linuxd00 on 2010-05-28
Hi,
i have one big problem.

Since i installed 9.10 (and it persists in 10.4) whenever i generate traffic over Wifi my systems slows down to the point of freeze.

Be it downloading system updates or Browsing the net (even simply listening to traffic with wireshark) the system will slow down and if the speed is high it will fully freeze.

i can tell its wifi because it only happens when generating traffic and when using a LAN cable the laptop will behave normally.
And i dont think its broken because in windows i have no problem.

when updating the system i get 56k speeds. It seems the system pauses between each packet... using cable it roars up to 1,7MB/s. HELP!

I have a IBM X31.

For my Wifi card, lshw show this:

```

Wireless interface
/0/100/1e/2


product: Atheros AR5001X+ Wireless Network Adapter [168C:13]
vendor: Atheros Communications Inc. [168C]
bus info: pci@0000:02:02.0
logical name: wlan0
version: 01
serial: [censored]
width: 32 bits
clock: 33MHz
capabilities:
	Power Management,
	bus mastering,
	PCI capabilities listing,
	ethernet,
	Physical interface,
	Wireless-LAN
configuration:
	broadcast: yes
	driver: ath5k
	ip: 192.168.178.37
	latency: 168
	maxlatency: 28
	mingnt: 10
	multicast: yes
	wireless: IEEE 802.11bg
resources:
	irq: 11
	memory: c0200000-c020ffff

```

---

### Post by linuxd00 on 2010-05-29
solved here:

[http://ubuntuforums.org/showthread.php?t=1496577](http://ubuntuforums.org/showthread.php?t=1496577)

i made a new thread because this problem might interest a lot of people

---

