---
title: "[SOLVED] individual paid support?"
date: 2008-10-30
forum: General Help
---

### Post by phmadore on 2008-10-30
I am looking for someone to help me make my wireless card work for around $20. I have no idea where to turn. Help?

---

### Post by PsychedelicReaction on 2008-10-30
model?

---

### Post by phmadore on 2008-10-30
The card is a "linksys wireless-g 2.4ghz 802.11g with speedbooster" the actual nomenclature being the "WPC54GS ver.2." I'm running 8.04 on a Compaq Presario 2100. How can I find out if the card is even in operational order?

Thanks!

---

### Post by teaker1s on 2008-10-30
Applications>Accessories>Terminal

```
iwconfig 
``` post output please

```
sudo lspci -v 
``` post output please


I think you need this page [https://help.ubuntu.com/community/WifiDocs/LinksysWPC54G]("https://help.ubuntu.com/community/WifiDocs/LinksysWPC54G")

---

### Post by phmadore on 2008-10-30
Note: didn't have wireless card in when I booted this last...

[blockquote]lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11g  ESSID:"MADORE"  
          Mode:Managed  Channel:0  Access Point: Not-Associated   
          Tx-Power=0 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0[/blockquote]


And

[blockquote]
phm@phm-linux:~$ sudo lspci -v
[sudo] password for phm: 
00:00.0 Host bridge: ATI Technologies Inc RS200/RS200M AGP Bridge [IGP 340M] (rev 02)
	Flags: bus master, 66MHz, medium devsel, latency 64
	Memory at d4000000 (32-bit, prefetchable) [size=64M]
	Memory at d0005000 (32-bit, prefetchable) [size=4K]
	Capabilities: [a0] AGP version 2.0

00:01.0 PCI bridge: ATI Technologies Inc PCI Bridge [IGP 340M] (prog-if 00 [Normal decode])
	Flags: bus master, 66MHz, medium devsel, latency 99
	Bus: primary=00, secondary=01, subordinate=01, sec-latency=68
	I/O behind bridge: 00009000-00009fff
	Memory behind bridge: d0300000-d03fffff
	Prefetchable memory behind bridge: d8000000-dfffffff

00:02.0 USB Controller: ALi Corporation USB 1.1 Controller (rev 03) (prog-if 10 [OHCI])
	Subsystem: Hewlett-Packard Company Unknown device 002a
	Flags: bus master, medium devsel, latency 64, IRQ 10
	Memory at d0000000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: [60] Power Management version 2

00:06.0 Multimedia audio controller: ALi Corporation M5451 PCI AC-Link Controller Audio Device (rev 02)
	Subsystem: Hewlett-Packard Company Unknown device 002a
	Flags: bus master, medium devsel, latency 64, IRQ 5
	I/O ports at 1000 [size=256]
	Memory at d0001000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: [dc] Power Management version 2

00:07.0 ISA bridge: ALi Corporation M1533/M1535 PCI to ISA Bridge [Aladdin IV/V/V+]
	Subsystem: ALi Corporation ALi M1533 Aladdin IV/V ISA Bridge
	Flags: bus master, medium devsel, latency 0
	Capabilities: [a0] Power Management version 1

00:08.0 Modem: ALi Corporation M5457 AC'97 Modem Controller (prog-if 00 [Generic])
	Subsystem: Hewlett-Packard Company Unknown device 002a
	Flags: medium devsel, IRQ 10
	Memory at d0002000 (32-bit, non-prefetchable) [size=4K]
	I/O ports at 1400 [size=256]
	Capabilities: [40] Power Management version 2

00:0a.0 CardBus bridge: O2 Micro, Inc. OZ601/6912/711E0 CardBus/SmartCardBus Controller
	Subsystem: Hewlett-Packard Company Unknown device 002a
	Flags: bus master, stepping, slow devsel, latency 168, IRQ 11
	Memory at d0003000 (32-bit, non-prefetchable) [size=4K]
	Bus: primary=00, secondary=02, subordinate=05, sec-latency=176
	Memory window 0: 30000000-33fff000 (prefetchable)
	Memory window 1: 34000000-37fff000
	I/O window 0: 00001800-000018ff
	I/O window 1: 00001c00-00001cff
	16-bit legacy interface ports at 0001

00:10.0 IDE interface: ALi Corporation M5229 IDE (rev c4) (prog-if fa)
	Subsystem: Hewlett-Packard Company Unknown device 002a
	Flags: bus master, medium devsel, latency 32
	[virtual] Memory at 000001f0 (32-bit, non-prefetchable) [disabled] [size=8]
	[virtual] Memory at 000003f0 (type 3, non-prefetchable) [disabled] [size=1]
	[virtual] Memory at 00000170 (32-bit, non-prefetchable) [disabled] [size=8]
	[virtual] Memory at 00000370 (type 3, non-prefetchable) [disabled] [size=1]
	I/O ports at 2000 [size=16]
	Capabilities: [60] Power Management version 2

00:11.0 Bridge: ALi Corporation M7101 Power Management Controller [PMU]
	Subsystem: Hewlett-Packard Company Unknown device 002a
	Flags: medium devsel

00:12.0 Ethernet controller: National Semiconductor Corporation DP83815 (MacPhyter) Ethernet Controller
	Subsystem: Hewlett-Packard Company Unknown device 002a
	Flags: bus master, medium devsel, latency 90, IRQ 10
	I/O ports at 2400 [size=256]
	Memory at d0004000 (32-bit, non-prefetchable) [size=4K]
	[virtual] Expansion ROM at 38000000 [disabled] [size=64K]
	Capabilities: [40] Power Management version 2

01:05.0 VGA compatible controller: ATI Technologies Inc Radeon IGP 330M/340M/350M (prog-if 00 [VGA controller])
	Subsystem: Hewlett-Packard Company Unknown device 002a
	Flags: bus master, stepping, fast Back2Back, 66MHz, medium devsel, latency 66, IRQ 10
	Memory at d8000000 (32-bit, prefetchable) [size=128M]
	I/O ports at 9000 [size=256]
	Memory at d0300000 (32-bit, non-prefetchable) [size=64K]
	[virtual] Expansion ROM at d0320000 [disabled] [size=128K]
	Capabilities: [58] AGP version 2.0
	Capabilities: [50] Power Management version 2

02:00.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)
	Subsystem: Linksys Unknown device 0049
	Flags: bus master, fast devsel, latency 64, IRQ 11
	Memory at 34000000 (32-bit, non-prefetchable) [size=8K]
[/blockquote]

---

### Post by phmadore on 2008-10-30
ALso, I've tried all the things I can on my own, but none of it seems to work for me... I'm not sure if I'm doing something fundamentally wrong or what.

---

### Post by teaker1s on 2008-10-30
forums died- looking at the situation you have linksys product which will need ndiswrapper to work plus windows driver-link in previous post

or I can see
[COLOR="Red"]02:00.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)[/COLOR] 
Which if you go into the system tab and select administration>restricted drivers- you should be able to make the broadcom work with a couple of clicks and a reboot.

Also a nice troubleshooting guide:-[https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide]("https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide")

---

### Post by shaggy999 on 2008-10-30
Somebody came to me with this card about a month ago. I could not get this card to work in linux, even with ndiswrapper. But then I also couldn't get it to work in Windows, either. Perhaps the card was damaged, I don't know.

---

### Post by phmadore on 2008-10-30
> **teaker1s said:**
> forums died- looking at the situation you have linksys product which will need ndiswrapper to work plus windows driver-link in previous post

or I can see
[COLOR="Red"]02:00.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)[/COLOR] 
Which if you go into the system tab and select administration>restricted drivers- you should be able to make the broadcom work with a couple of clicks and a reboot.

Also a nice troubleshooting guide:-[https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide]("https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide")

Okay so I enabled the driver. Then I unplugged the cat5 cable and rebooted the computer and tried to open a webpage and it didn't work. What am I doing wrong?

Thanks so far!

---

### Post by phmadore on 2008-10-30
By the way is there any suggestion of a relatively cheap alternative wireless card?

---

### Post by teaker1s on 2008-10-30
if your wireless network is encypted then you will need a key. firstly check wireless switch is on if laptop and you want to post 
```
iwconfig
``` lets see if it's powered up

---

### Post by phmadore on 2008-10-31
phm@phm-linux:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11g  ESSID:"MADORE"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=27 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

---

### Post by phmadore on 2008-10-31
My wireless is set up so it will only accept listed mac addresses... checking if this one is already on there... but the real question is how do I manage my wireless card in ubuntu...

---

### Post by phmadore on 2008-10-31
phm@phm-linux:~$ iwlist wlan0 scanning
wlan0     No scan results

---

### Post by phmadore on 2008-10-31
phm@phm-linux:~$ iwlist wlan0 scanning MADORE
Invalid scanning option [MADORE]
phm@phm-linux:~$ iwlist wlan0 scanning "MADORE"
Invalid scanning option [MADORE]
phm@phm-linux:~$ iwlist wlan0 "MADORE" test
iwlist: unknown command `MADORE' (check 'iwlist --help').
phm@phm-linux:~$ iwlist wlan0 essid madore
iwlist: unknown command `essid' (check 'iwlist --help').
phm@phm-linux:~$ iwlist wlan0 madore test
iwlist: unknown command `madore' (check 'iwlist --help').
phm@phm-linux:~$ iwlist wlan0 madore
iwlist: unknown command `madore' (check 'iwlist --help').
phm@phm-linux:~$ iwlist wlan0
iwlist: unknown command `wlan0' (check 'iwlist --help').

---

### Post by phmadore on 2008-10-31
Umm...

[IMG]http://freemadore.info/img/wireless-ss.png[/IMG]

---

### Post by phmadore on 2008-10-31
So when I hit configure, it tells me the device doesn't exist... !

---

### Post by phmadore on 2008-10-31
Okay, I definitely just got it to show me my network and another wireless network in the area... And I selected mine, and on my router the mac address is authorized, and so I rebooted and still nothing unless I plug in my cat5 cable. This is madness! It sees the networks, I've selected them, but something is still wrong. What could it be? Anybody? OH I'M SO CLOSE...

---

### Post by teaker1s on 2008-10-31
your trying to use network tools which is network testing not [COLOR="Red"]network[/COLOR]
I'm using Debian kde at the moment, but you should find network System>administration>network

iwconfig shows we have both wireless card and its got tx power-so we should be able to connect.

If your ethernet is plugged in it overrides wireless. 

Also on desktop panel by clock if you can see an icon with a cross and computer screen network-manager-applet.
if you can't see it
```
sudo nm-applet
```

find your mac address
```
ifconfig
```

example is Ethernet-but you can see hwaddr=mac

> eth0 Link encap:Ethernet HWaddr 00:0C:29:A8:D0:FA

you say your wireless is mac filtered, you therefore have two choices 
1) turn off mac filtering (even if it's just for testing)
2) Use the above command ```
ifconfig
``` to find the wireless mac and register it with your network device(router or access point)

---

### Post by phmadore on 2008-10-31
I'm not going to pretend that I have the slightest clue how, but now it's working! If ever you run into another total retard who doesn't know what they're doing--run them through the same basic steps and then tell them to reboot unplugged--and bam, it works! THANK YOU SO MUCH! (I did turn off the mac address thing; what are my security options?)

---

### Post by teaker1s on 2008-10-31
network-manager will support wep, passphrase and asci and hex.
Now I don't have your wireless card, but you should find that wpa will also work on restricted drivers if not it will need wpa_supplicant setting up

we also have wireless assistant and wifi radar available in repositories as alternatives.

Welcome to the forums,they are a really great place to find out about linux-community is the best I've found.
As you can see I joined in 2005-I still learn new things every day.

---

### Post by phmadore on 2008-10-31
Okay, nevermind. All I had to do was redo my whole "setup access list" thing on the Netgear Router, add the three available mac addresses (one mac laptop, one linux laptop, and one windows laptop), and then "turn access control on," and I'm good to go! Sweet! I'm quite happy about this.

Thank you so very much!

---

### Post by phmadore on 2008-10-31
> **teaker1s said:**
> network-manager will support wep, passphrase and asci and hex.
Now I don't have your wireless card, but you should find that wpa will also work on restricted drivers if not it will need wpa_supplicant setting up

we also have wireless assistant and wifi radar available in repositories as alternatives.

Welcome to the forums,they are a really great place to find out about linux-community is the best I've found.
As you can see I joined in 2005-I still learn new things every day.

Thank you for the welcome, and like I say, I'm now good to go. My Mac gives me an issue every time I try to set a passphrase, although that was also with 10.3, and now I've upgraded to 10.4, but since it's all working now, I think I'll leave it alone. I think my example would be good for someone completely new--although I've been at this for a little while--and I'm going to go ahead and post a blog entry about it so people know where to turn if they happen upon my little corner of the retarded internet... This was my last barrier to happily using Ubuntu... I'm quite pleased...

---

### Post by teaker1s on 2008-10-31
If you can mark the thread solved with the thread tools it would be great.

I've sent you a friendship request,if you add me you can always post another thread and pm me if you'd like a little assistance.:popcorn:

regards

Dan

---

