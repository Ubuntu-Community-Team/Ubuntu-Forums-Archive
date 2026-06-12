---
title: "Network controller not turning off after shut down"
date: 2014-09-27
forum: Hardware
---

### Post by argonvegell on 2014-09-27
I just upgraded from Xubuntu 12.04 to 14.04, and I noticed that whenever I shut down my PC, the LAN light of my modem doesn't turn off and the Network controller behind my PC, it's light doesn't turn off as well, I think this is a bug, because this didn't happen in 12.04, and because I use a voltage regulator to protect my PC from power surges, the modem LAN light and Network controller only turn off when I switch the AVR off after shutting down the PC. Any ideas why this is happening? After running "lspci -nn -d 14e4:" on the terminal, this is the model of my Network controller, Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller [14e4:4318] (rev 02)

---

### Post by JKyleOKC on 2014-09-27
It's possible that the network adapter in your PC has the "Wake on LAN" feature that allows the box to be turned on remotely via a command received over the LAN. For that to work, the network adapter has to remain powered up after the rest of the box is turned off. It's also possible that some change in a network driver is causing such a feature to be activated, when it never was before.

I'm seeing a slightly similar situation in my newly installed 14.04 system, that didn't happen with 12.04. In my case, one of the network adapters (the box has three, but only two are in use and the third is a spare) introduces several seconds of delay after powering on, to initialize the PXE boot-over-LAN feature -- which I do not use and don't know how to disable. What's more, that delay is coming from the **spare** network card! With 12.04, that did not happen during boot-up, so I suspect we may be seeing two different aspects of the same change. I don't know whether to call it a bug or not, though...

---

### Post by argonvegell on 2014-09-27
> **JKyleOKC said:**
> It's possible that the network adapter in your PC has the "Wake on LAN" feature that allows the box to be turned on remotely via a command received over the LAN. For that to work, the network adapter has to remain powered up after the rest of the box is turned off. It's also possible that some change in a network driver is causing such a feature to be activated, when it never was before.  I'm seeing a slightly similar situation in my newly installed 14.04 system, that didn't happen with 12.04. In my case, one of the network adapters (the box has three, but only two are in use and the third is a spare) introduces several seconds of delay after powering on, to initialize the PXE boot-over-LAN feature -- which I do not use and don't know how to disable. What's more, that delay is coming from the **spare** network card! With 12.04, that did not happen during boot-up, so I suspect we may be seeing two different aspects of the same change. I don't know whether to call it a bug or not, though...    Thanks for the reply, how do I disable "Wake on LAN" feature? And is my PC safe if the Network controller doesn't turn off during shut down? Side note, how do you make paragraphs on your post, my text comes as a continous block.

---

### Post by JKyleOKC on 2014-09-27
Sorry but I don't know how to disable it myself. However your PC should be safe in any event, particularly if you're using a router between the PC and the actual modem (which may be in the same box as the router; many ISPs these days furnish "gateway" units that combine both functions).

I make the paragraphs by hitting Enter twice, to leave a blank line between them. The HTLM language that controls all web displays treats single carraige returns or line feeds the same as blank spaces, in order to look best on all sizes of displays.

---

### Post by argonvegell on 2014-09-28
I seemed to have solved my own problem.
[http://www.hecticgeek.com/2012/09/di...n-your-laptop/]("http://www.hecticgeek.com/2012/09/disabling-wake-on-lan-in-ubuntu-might-save-a-tiny-bit-of-power-on-your-laptop/")

I followed the steps outlined in this site and WOL is disabled.

---

### Post by JKyleOKC on 2014-09-28
Many thanks! You've solved my problem also, I think!

While the link you give doesn't say so, the procedure also works for Trusty...

---

### Post by almoya72 on 2015-09-08
I'm still experiencing this problem after disabling wol. How can I turn off power to the nic when shutting down?

---

