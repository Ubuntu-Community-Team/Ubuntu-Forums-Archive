---
title: "broadcom wireless - 9.04"
date: 2009-06-20
forum: Hardware
---

### Post by chrisfaulkner on 2009-06-20
Hello

I am trying to get the onboard wireless card (Broadcom 4306) to connect to the wireless network in my home. I'm running the latest version and have downloaded the updates via a wired connection. 

When I first installed, it wouldn't connect at all - I could see the networks in range but no connections were possible. So I found this in this forum.

sudo /usr/share/b43-fwcutter/install_bcm43xx_firmware.sh

Now this helped because I could now connect to my wireless network (although I can't see any of the other networks in range anymore but I could let that one go !).

However, the default wireless network setup just asks for the key and that is it. So it creates a network connection profile, tells me that I am connected to my network but I haven't got a properly assigned IP address. This seems to be because by default the IP comes from something called "Shared to other computers" rather than DHCP. The eth0 connections defaults to "DHCP" which is what I want. So at this point I am connected to the network but haven't got an IP address. I can go to the network connections and fix this but it doesn't seem to reapply the settings and reconnect.

When I reboot, whatever happened during that firmware install is lost so I am back at the beginning.

I now see Broadcom STA and Broadcom B43 in the hardware drivers list - which one should I use ?

I am enjoying using Ubuntu and desperately want to get this fixed.

Thanks for any help you can give.

Chris

---

### Post by IraGainesUK on 2009-06-29
Hey Chris, 

Ive been having a few problems with my Broadcom WiFi too (BCM4328 802.11a/b/g/n).  I've done some reading around, and the STA driver is definitely the one to use.  The other is a community sponsored attempt to create drivers for broadcom cards before broadcom brought out the STA driver (and dedicated drivers are always better IMHO).

The problem I was having was that the range of the wifi was much lower when the router was transmitting at draft-n speeds, and just wouldnt connect in rooms that connect just fine when using Windows Vista. 

To fix it I just logged into the router admin page (usually 192.168.0.1 or similar) and changed the transmit wifi speed to 'g only'.  This solved the range/connection problem for now, however Im not happy not being able to use the faster speeds and so wouldnt call it a permanent solution.  I guess thats why they call it 'draft-n' for now, huh...

Anyway, hope this helps with your problem, and apologies if not (im still learning Linux... :) )

Ira

---

### Post by sensory on 2009-06-29
> **IraGainesUK said:**
>  To fix it I just logged into the router admin page (usually 192.168.0.1 or similar) and changed the transmit wifi speed to 'g only'.  This solved the range/connection problem for now, however Im not happy not being able to use the faster speeds and so wouldnt call it a permanent solution.  I guess thats why they call it 'draft-n' for now, huh...
For some weird reason, switching to 'g only' fixed my problem completely.

I've been having a very weird speed issue using the b43 drivers with my Broadcom 4311 card. It'll connect just fine, but the download speed will be 1Mbit as opposed to the 10Mbit it's meant to be. I tried using ndiswrapper but even though I blacklisted the b43 driver it would always load first and take control of my wireless card.  Not only was the speed low, but when browsing it would 'stall' for about 3-4 seconds before loading the page, which got ever more frustrating as the day went on.

I've been searching high and low and none of the solutions seemed to help.

For now, your solution has done the job! My speeds are back to what they should be and I'm still using the b43 drivers. Thanks for your post. :D

---

### Post by rmhartman on 2009-06-30
> **IraGainesUK said:**
> Hey Chris, 

Ive been having a few problems with my Broadcom WiFi too (BCM4328 802.11a/b/g/n).  I've done some reading around, and the STA driver is definitely the one to use.  The other is a community sponsored attempt to create drivers for broadcom cards before broadcom brought out the STA driver (and dedicated drivers are always better IMHO).


Ok, I've got a Vostro 1310, but the wireless is the same as yours (4328).  Network shows it as an 'unknown interface'.  'Hardware drivers' (Jockey) shows that I have the Broadcom STA wireless driver "activated but not currently in use".  

Where do I go from here?

---

### Post by chrisfaulkner on 2009-07-03
Thanks VERY much for the reply. That is helpful - I'll give it a go and let you know.  Problem is that some of my cards in the house are "B" still 

Great that you took the time. This community is great

---

### Post by Pogibry on 2009-07-03
i forgot which driver i used but it wouldn't see my network. I then manually created the connection and then it connected to it just fine (i can't remember if i was able to connect to the net or not). I'm pretty sure i used the the recommended sta driver as well.

---

