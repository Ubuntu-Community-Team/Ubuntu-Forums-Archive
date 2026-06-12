---
title: "Got Linksys PCI card to discover, but doesn't connect."
date: 2014-12-19
forum: Hardware
---

### Post by Sam_Agustini on 2014-12-19
Machine is an IBM ThinkCentre A51 3Ghz PIV 1.5GB RAM, UBUNTU 14.04 LTS. Card is a Linksys WNP11 PCI WiFi.

I have followed the very good directions from these posts.

[https://help.ubuntu.com/community/BroadcomSTA](https://help.ubuntu.com/community/BroadcomSTA)(Wireless)

[http://askubuntu.com/questions/55868/installing-broadcom-wireless-drivers](http://askubuntu.com/questions/55868/installing-broadcom-wireless-drivers)

[https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsLinksys#WMP54G](https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsLinksys#WMP54G)

I have also rolled-in the blacklist and "ignore" status for IPv6. Network can be scanned and I see all my neighbors Access Points (and mine). I configure mine but am unable to connect via infrastructure or Ad-Hoc. Wireless Router is an Exfinity Comcast unit. Cisco I think. it has a 2.4Ghz b/g channel and a 5Ghz A/N channel. I set-up the encryption to [FONT=Times New Roman][SIZE=3][COLOR=#000000][/COLOR][/SIZE][/FONT][FONT="Arial"][COLOR=#000000]WPA-PSK(WPA2 AES) due to the card being older.[/COLOR][/FONT]
[FONT=Times New Roman][SIZE=3][COLOR=#000000][/COLOR][/SIZE][/FONT]

my lspci command with a grep on 14e4 tells me I have a 
Broadcom Corp BCM4301 [14e4:4301] (rev 02)

In the Network app, I can select and click connect but it will fail to connect. 

I have installed the Synaptics package Manager and have installed the 

b43-fcutter    ver 1:018-2
firmware-b43legacy-installer    ver 1:018-2

Suggestions?

---

### Post by Sam_Agustini on 2014-12-28
Friday I tried the instructions here: [http://askubuntu.com/questions/457009/wifi-wont-work-on-14-04](http://askubuntu.com/questions/457009/wifi-wont-work-on-14-04)
My next step was to try the ndiswrapper. My other thought was that the card is old and probably only 801.11b and I'm out of range, or maybe it doesn't support WPA2. So I had my nephew over Saturday evening and he suggested something novel (which I hadn't thought of). To try and see if I could connect via his handheld HTC smartphone in "hotspot" mode. 
He turned it on, my machine discovered it, I clicked <Connect>, he provided the passphrase and "boom" I'm connected! I launch Firefox and get my Home page!

So it would seem that the card IS actually working and as the HTC hotspot encryption is wpa/wpa2, I now know that that isn't the issue either. Unfortunately, I am not aware of any "Eventlog" tool in Ubuntu that might give me a clue as to what is actually the issue.. I'm thinking maybe it only operates inb "b" mode as I have an HP 1100w sitting right next to it that I can print to from the same distance and around the corner. So I will first try to extend the antenna or get an access point set-up in the middle.

---

### Post by weatherman2 on 2014-12-28
If the card is really 802.11b (really old), it's possible your Comcast router isn't configured to allow 802.11b connections.   You may be able to change that in the router configuration by logging into the router.  I think allowing for such old, slow connections can slow everyone else connected down, so sometimes only the faster standards like 802.11n are allowed.  Even 802.11g is pretty old now.

Have you considered spending $5 USD on a little USB 802.11n wireless dongle instead?   You can find them on eBay and Amazon.  I haven't bought any in a while - dig up one that has good Ubuntu support.  (The key is the chipset.)

---

### Post by Sam_Agustini on 2015-02-22
weatherman2, you were exactly correct! After installing an antenna extension cable and getting signal from good to excellent, I still could not connect. So I scrutinized the gateway settings some more. I edited the 2.4GHz connection in the xfinity router and there is a drop-down that was set to 802.11g/n/a so I set it to 802.11 b/g/n. So definitely a MAJOR part of the problem! So I would get connected, but then it would immediately drop. Lastly, I removed the drivers using the Symantec Package Manager I installed previously. This was in prep to go the ndiswrapper route (it sat like this for a few weeks as I lost interest). I decided to give it one more try. I hooked-up to network via Ethernet. Using the package manager, I re-installed the bcm43 firmware, b43 fwcutter, and the b43 legacy installer. Reboot. Double-check logon creds for the wireless connection. Still not quite. I changed the connection type to Ad Hoc. It's working now and connection is stable. It pays to persevere and be methodical!

---

