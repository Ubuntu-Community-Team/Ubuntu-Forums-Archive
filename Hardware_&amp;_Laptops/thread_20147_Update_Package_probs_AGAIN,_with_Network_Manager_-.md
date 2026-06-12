---
title: "Update Package probs AGAIN, with Network Manager - Gnome"
date: 2005-03-15
forum: Hardware &amp; Laptops
---

### Post by jMack on 2005-03-15
Grrrr....

I REALLY want to use ubuntu on my laptop, but I've had to reinstall TWICE now, I have sound and network issues still and getting more frustrated as I go.

My problems always stem from updating files in synaptic.

The latest one now doesn't let me connect to the internet at all anymore.  I have a Toshiba Satilite Laptop using a D-Link wireless card (athos.. chip).  Had complete connectivity 10 minutes ago, now...funny.  

I run iwlist ath0 scan, and can see the router.
I can configure my NetworkManager and it shows that its active and connected.

But I cannot ping anything on the system.  GAIM doesn't connect, nothing.
I show 60-70% signal strength in my toolbar.

My issue probably stems with trying to install network-manager-gnome found at:
[http://people.ubuntu.com/~thom/network-manager/](http://people.ubuntu.com/~thom/network-manager/)

I installed it as it said, but I noticed that I was getting an error at boot-up:
>  relocation error /user/sbin/NetworkManager  undefined symbol: iw_scan 
I saw somewhere someone talking about an error like this, to which someone said to run update.
At this stage network-manager-gnome wasn't working (far as I could tell), but I still had internet connectivity.

When I ran the Smart Update, I noticed a 'wireless' package got updated, along with firefox, and numerous other unknown lib packages.  And after a reboot; no internet connectivity.

I'm always bouncing back to my windoz box to troubleshoot Ubuntu.  I REALLY like it so far, its just that there are packages out there that I really want like network-manager-gnome cuz of wireless quick-change abilities, and VLC for DVD playback (no sound right now)...etc.

Any help is appreciated.

---

### Post by eternity on 2005-03-15
try disable NetworkManager and run this comands instead:

iwconfig ath0 essid YourRouter key WEPKeyIfYouUseEncryption
dhclient ath0

If things work you should get an ip-adress and be able to ping your router.

---

### Post by jMack on 2005-03-15
how do I disable Network Manager?

yea, bit of a noob.

---

### Post by jMack on 2005-03-15
I removed the connection in Network Manager, run the 2 commands you mention, and get this:
> 
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 15
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 19
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 12
No DHCPOFFERS received.
No working leases in persistent database - sleeping


I have powered down/up my wireless router....should I try it again?

EDIT
* there was some more feedback after running the dhclient ath0 command, but it looked like basic stuff. *

---

### Post by jMack on 2005-03-15
OK, here's the whole thing (typing it out!)
> 
Internet Systems....
Copyright 2004 ....
All rights reserved.
For info....

sit0: unknown hardware address type 776
sit0: unknown hardware address type 776   (yes, said twice)
Listening on LPF/ath0/00:0d..6b
Sending on  LPF/ath0/00:0d..6b
Sending on Socket/fallback
 DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 15
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 19
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 12
No DHCPOFFERS received.
No working leases in persistent database - sleeping


---

### Post by eternity on 2005-03-15
You wlan card does for some reason not retrive an ip adress from your router...

Post your output of:
iwconfig ath0
iwlist ath0 scan

after you have run my above mentioned commands

---

### Post by jMack on 2005-03-15
Typing out:

iwconfig ath0:

> 
ath0  IEEE 802.11g ESSID:"MYROUTER"
Mode: Managed  Frequency: 2.432GHz  Access Point: FF:FF:FF:FF:FF:FF
Bit Rate:1Mb/s  Tx-Power:50dBm  Sensitivity=0/3
Retry: off  RTS thr: off Fragment thr: off
Encryption key:XXmykeyXX  Security mode: restricted
Power Management: off
Link Quality=11/94  Signal level--84 dBm  Noise level=-95dBm
Rx invalid nwid:1  Rx invalid crypt: 0  Rx invalid frag:0
Tx excessive retraies:0  Invalid misc: 0  Missed beacon:0


The only things above that I changed was my ESSID, and the encryption key.  All other things should be spot on, INCLUDING the Access Point mac address, which looks suspect.

next command:  iwlist ath0 scan
this looks interesting, since I don't see the typical ESSID!

> 
ath0 Scan completed:
Cell 01 - Address: 00:11:95:40:94:41
ESSID:""
Mode:Master
Frequency:2.437GHz (Channel 6)
Quality=15/94  Signal level=-80dBm
Encryption key: on
Bit rate:1Mb/s
....
Bit Rate:54Mb/s
Extra:bcn_int=100



it looks to me that theres a mac issue, and now an issue with my router?  Strange... 
Got an interpretation?

---

### Post by eternity on 2005-03-15
Have you tried the wlan card in windows or have you tried using the wlan card with another AP?

The MAC address should definitely not be FF:FF:..., the wlan card does obviously not find the router. To me this looks like the router is causing the problem...

---

### Post by jMack on 2005-03-15
My laptop is set to dual-boot: XPhome + Ubuntu

I just rebooted and brought up XP
It connected to the router immediately, and I had full interenet access.

I restarted and brought-up Ubuntu
Still no internet connectivity.


Definately an Ubuntu and not a Router issue....it maps mac addresses with LAN ip's (D-link 524+ Router) like normal routers, so there shouldn't be an issue moving from one to another.  Strange!

My next step was to uninstall networkmanagergnome in synaptic.  Agreed?

EDIT
[i]
Is there anything in Linux like XP for Restore Points?  Curious...[/i]

---

### Post by eternity on 2005-03-15
Well, NetworkManager is not causing the problem so unstalling it won't do any difference. AFAIK NetworkManager use the wireless tools that you used in the command line and present it as a nice gui.

I would recommend to uninstall NetworkManager and try get things working in command line and then if needed install a gui (I prefer netapplet as it's more stable, at least on my system).

---

### Post by jMack on 2005-03-15
OK, I'm totally confused now.

I went into Synaptic and uninstalled TWO things:

NetworkManager and NetworkManagerGnome.

I removed them both as 'Removed' but not 'Completely Removed', which i suspect removes it and all it's dependancies.

I actually removed the ...Gnome one first, rebooted and retried connecting.  Nope.
Then I removed NetworkManager.  I then rebooted.  CONNECTION!!!????!!!

If I go Computer - SystemConfiguration - Networking, it STILL LOADS.
All my settings were there, all good.  It's like I never left.

Strange...very strange....

Can you suggest a program to easily switch between wireless access points having different ESSID's and WEP's?  This is the whole reason I went down this road.

And by the way, thanks for getting internet connectivity back to my Laptop, even if I don't totally understand why.

---

### Post by jMack on 2005-03-16
When I installed NetworkManagerGnome, did it also install NetworkManager?
I could've sworn that it was already installed b4.

Again,  what is a good program that I could use to easilly switch between different wireless connections?  NetworkManager is obviously not the way to go :)
I'd like it as a gui if possible too.

---

