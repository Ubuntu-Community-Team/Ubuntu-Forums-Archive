---
title: "Compaq Presario V2000 - non-functioning wireless"
date: 2006-10-15
forum: Hardware &amp; Laptops
---

### Post by Bosonator on 2006-10-15
Hello,

Finally got around to installing Ubuntu Dapper on my Presario laptop. Very impressed at how smoothly most things went - even the special laptop buttons worked right away!

Here's the "but": I can't get wireless capabilities working. "System>Administration>Networking" shows my card on the list of connections, but it won't let me activate it (it just tries for a while, then does nothing). I've heard that some people say using ndiswrapper makes it work, but others say that this is unnecessary with Dapper Drake.

Points of interest/clarification: 
1. my laptop has a button for toggling the wireless function on and off. It won't respond to being pressed at all.
2. In the panel, I have a warning message saying: "Please contact your system administrator to resolve the following problem: SIOCGIFFLAGS error: No such device."
3. In the "Networking" window, I can press "activate", and it will eventually say that my wireless connection is activated, but I can't connect to the internet through it.
4. In the "Properties" window for my wireless connection, I give it my SSID, but it asks for a WEP key. My router is configured to use WPA (shared passphrase), but not WEP. 
5. See below for lshw output.

Thanks if anyone can help!
- Bosonator



lshw output:  
------------
*-network:1 DISABLED
       description: Wireless interface
       product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 2
       bus info: pci@05:02.0
       logical name: eth1
       version: 02
       serial: 00:14:a5:71:38:2b
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master ethernet physical wireless
       configuration: broadcast=yes driver=bcm43xx multicast=yes wireless=IEEE 802.11b/g
       resources: iomemory:c0204000-c0205fff irq:225

---

### Post by compwiz18 on 2006-10-26
[http://ubuntuforums.org/showthread.php?t=197102](http://ubuntuforums.org/showthread.php?t=197102)

if you still need help, that should do it for bcm4318 wireless cards that come in V2000s

---

### Post by nappy1877 on 2006-11-02
I have a Compaq Persario V2000 and the wireless card is Intel PRO/Wireless 2200BG. I have WPA2 encryption on my card and trying to find some sort of guide to set up the encryption. Also my WiFi button works, but does not light up when pressed. Other than that, Ubuntu works great.

---

### Post by Bosonator on 2006-11-03
Are you using network-manager along with knetworkmanager (KDE) or network-manager-gnome? I think that both of these support WPA2.

---

### Post by sarmadzhiev on 2006-11-03
Did you set up the bcm43xx module?

You must extract the firmware first from your windows driver I believe the name of it is bcmw15.sys or something like that. You may find it in your c:\windows\drivers directory. Copy this file to the linux and use fwcutter to extract the firmware. It will produce several bcm_microcode*.fw files. Copy them in  /lib/firmware. 
Then restart and it will work. 

To be sure check the System Log for line with bcm43xxx. It should be only one line that is successful. 

installing the fwcutter -> the package name I don't remember but you may find is in Synaptic with search for bcm or cutter.

---

### Post by salvador_luna on 2006-12-13
I have my wireless card working perfect with 6.10.

I used these instructions:

1) [http://www.ubuntuforums.org/showthread.php?t=197102&highlight=wireless](http://www.ubuntuforums.org/showthread.php?t=197102&highlight=wireless)

2) [http://www.ubuntuforums.org/showthread.php?t=190177&highlight=wireless](http://www.ubuntuforums.org/showthread.php?t=190177&highlight=wireless)

I receive several errors while following the first How to, so I followed the second one and, when i reboot my machine, i push the button to turn on the wireless and it worked fine (even the light).

I'm a new user of ubuntu so, when I followed the instructions of the first How To an get the errors, I didn't undo anything, just followed the second one.

Sorry if my English isn't clear, I speak spanish :D

---

