---
title: "Airlink101 AWLL6080 USB Works With Ndiswrapper"
date: 2007-10-31
forum: Hardware &amp; Laptops
---

### Post by JC Casiano on 2007-10-31
I purchased this USB adapter from Fry's for $25 (Halloween Sale), and it is working with ndiswrapper 1.38 under Kubuntu Feisty 2.6.20-16-386.  I downloaded the awll6080_drv_util.zip from Airlink101.com, extracted it, and then directed ndiswrapper to install using ../WinXP2K/rt2870.inf.  Then I edited /etc/modules, adding "ndiswrapper" so that the driver would be loaded when I dropped my laptop into it's docking station. \\:D/

I have not tested all of it's functionality, but at least it works at 48Mb with my Linksys router.

---

### Post by Gul Macet on 2007-11-04
Hi -

I just got the same setup from Fry's - an AR680W router and AWLL6080 USB card. For the latter, I'm using the latest drivers I downloaded from Airlink101 and the latest ndiswrapper (1.49).

Now, I've been trying to get just about any USB wireless device to work under Gutsy, so I'm not complaining by a longshot, but were you able to get the device to connect with 802.11n?

Mine seems stuck at 802.11g (the router confirms this). iwpriv doesn't complain when I try:

iwpriv wlan2 network_type n

but it appears to have no effect. And:

iwlist wlan2 rate 

only goes up to 54Mbps, which is what I'm connected at. Similarly,:

iwconfig wlan2 rate 300M

does nothing. It seems to be ignored, which is no surprise since, as I said, 300 isn't listed under iwlist.

Looks like there aren't a lot of people trying to use 802.11n with ndiswrapper. I'm wondering if it's a limitation of ndiswrapper or iwconfig. Ndiswrapper would seem to be the more likely culprit. Maybe the API mappings haven't caught up to whatever extensions NDIS uses for 802.11n?

Any ideas?

---

### Post by thunder.dude44 on 2008-02-04
I have this same card, just bought it at Fry's for like $20. I got it to work on my laptop with Windows XP. I'm trying to get it to work with my router in linux (Ubuntu 7.10), but I can't get the card to connect. The card connects to my router in Windows XP, but I can't seem to get it to connect to the network, even though I can see it listed in linux. The router is from my internet provider, SBC/Yahoo. It supports wireless b/g I believe. Any ideas as to how to fix this issue?

Update:
I got it to start connecting to networks. No idea how I did that. But it doesn't seem to want to stay connected. After a while, the connection will drop out and the card will stop blinking and just have a steady light on without blinking. So I don't know what to do. I can update or downgrade the ndiswrapper version manually instead of using the Ubuntu version, but other than that I'm at a loss as to how it stops connecting to the network. It's almost as if it just stops wanting to send or recieve info to and from the router. Also, another thing of note is that the Network Manager applet in gnome continues to say that the card is connected to the internet and has an IP Address even though it obviously isn't. I proved this by having a bittorrent program  and an IM client up and talking to people while I'm doing other things. Sure enough, after a while, the card stops blinking and I can't send or recieve messages or get on google and my torrents are stopped due to a disconnection. But the NM still says I'm connected. I don't know if this wil matter, but I thought I would also mention that the usb detection hangs after my card stops working, but it's fine before.

So, any ideas as to what to look for or where to look for the source of the problem?

---

### Post by mistere23 on 2008-03-09
Can someone please elaborate on how they got the AWLL6080 to work?  I got ndiswrapper to install the driver, but nothing on my system seems to recognize the device besides ndiswrapper.  I'm running Gutsy and I'm pretty new to linux and Ubuntu so I don't know that many commands or where to look in the GUI.

---

