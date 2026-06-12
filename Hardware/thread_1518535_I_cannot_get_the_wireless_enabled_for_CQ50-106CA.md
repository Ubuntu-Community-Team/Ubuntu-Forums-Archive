---
title: "I cannot get the wireless enabled for CQ50-106CA"
date: 2010-06-26
forum: Hardware
---

### Post by IsadorCJ on 2010-06-26
it's with an Atheros 5001 wireless Ethernet. the system can detect the hardware and showing: 
Wireless interface 
/0/14/0 


product: AR5001 Wireless Network Adapter [168C:1C] 
vendor: Atheros Communications Inc. [168C] 
bus info: pci@0000:07:00.0 
logical name: wlan0 
version: 01 
serial: 00:1f:e1:72:66:f8 
width: 64 bits 
clock: 33MHz 
capabilities: 
	Power Management, 
	Message Signalled Interrupts, 
	PCI Express, 
	MSI-X, 
	bus mastering, 
	PCI capabilities listing, 
	ethernet, 
	Physical interface, 
	Wireless-LAN 
configuration: 
	broadcast: yes 
	driver: ath5k 
	latency: 0 
	multicast: yes 
	wireless: IEEE 802.11bg 
resources: 
	irq: 23 
	memory: c2000000-c200ffff 
this device has been disabled 

As you guys can see at the last line, you can see " the device is disabled". but when I click on the network icon of ubuntu, the "enable wireless" turns to be grey and can never be clicked on to enable the wireless. Meanwhile, the hard-switch of the laptop, i.e. the blue little button beside the power button, is always on"in windows, the wireless is off when the button turns red, and on when it's blue". but in Ubuntu, it's been always blue...........I have no idea to open the wireless component.

---

### Post by IsadorCJ on 2010-06-26
plz help...i've tried the whole day long from blacklist or other stuff

---

### Post by IsadorCJ on 2010-06-28
really need some help over here

---

### Post by offshoredevelopment on 2010-06-28
> **IsadorCJ said:**
> plz help...i've tried the whole day long from blacklist or other stuff
I have just blacklisted the bcm4xx driver than re-did ndiswrapper and its like 10x faster . ndiswrapper works much better.

---

