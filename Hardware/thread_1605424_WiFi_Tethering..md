---
title: "WiFi Tethering."
date: 2010-10-25
forum: Hardware
---

### Post by Jrgifford on 2010-10-25
I have a Asus Eee PC 1001P running Ubuntu 10.10 Netbook remix. I want to use it to connect to a wifi network and act as a relay, somewhat like tethering. Is this possible?

---

### Post by kaspar_silas on 2010-10-25
Are you saying you want to connect via the wifi and then share the connection via wifi? That is certainly possible but you need two wireless adaptors one to receive and one to broadcast.

If you only have the built-in adaptor you could buy a USB wireless adaptor and then do something similar to the folowing page to share the connection.

[NetbookToHotspot-Link]("http://www.greenhughes.com/content/how-turn-your-netbook-3g-mobile-broadband-wifi-hotspot")

---

### Post by Jrgifford on 2010-10-25
Yes. That is exactly what I want to do. And I have a USB adapter, I just need to have a general idea of what hoops I need to jump through.

---

### Post by kaspar_silas on 2010-10-25
Working out how difficult something is before you start. Very wise and something I often wish I had done. Anyhow the hoops seemed pretty simple so I thought I would test them.

So I did this: 
1/ Plugged in my wireless USB adaptor
2/ Clicked the network manager 
3/ Selected "Create New Wireless Network" 
   and entered a wireless name and a wep passphrase.

I thought this should be working now. Sure enough my android phone detected a new wireless hotspot. However it could not connect it just hangs waiting for an ip address to be assigned.

Maybe there is a crucial step I missed out. I sort of assumed the "Create New Wireless" step was doing some stuff in the background like starting a dhcp server. 

Quick question to anyone else? Does this procedure work for you?

---

### Post by kaspar_silas on 2010-10-27
So no one has managed to make a wifi gateway using network manager?

---

### Post by Jrgifford on 2010-11-19
Sorry about taking so long to get back to you, had some real life stuff going on and I was too busy to reply. After some googling and tweaking, I was able to use this page as an outline:[https://help.ubuntu.com/community/Internet/ConnectionSharing#GUI Method via Network Manager (Ubuntu 9.10 and up)]("https://help.ubuntu.com/community/Internet/ConnectionSharing#GUI Method via Network Manager (Ubuntu 9.10 and up)"). And it works! Thanks for your help!

---

### Post by kaspar_silas on 2010-11-23
Hi,

No problem I totally forgot about this anyway.

That page pretty much had exactly what I was trying other than the magic words.
"wpa is not supported"
which explains all my previous problems

---

