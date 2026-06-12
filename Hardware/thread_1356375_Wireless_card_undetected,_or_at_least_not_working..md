---
title: "Wireless card undetected, or at least not working."
date: 2009-12-16
forum: Hardware
---

### Post by Omicron Machine on 2009-12-16
EDIT: The "real" wireless isn't nvidia, the one I put in there is apparently, "Intel PRO/Wireless 3945ABG Network Connection", model number "WM3945ABG".




Hello. I have an HP Pavillion dv6000, that came with a broadcom wireless card, which didn''t work, none of the usual fixes for broadcoms worked, and nothing anyone in any thread on it did changed anything at all. It was just very, very stubborn. 

I changed it for an nVidia card (apparently), which I couldn't get to work either, though it was rumoured to be more compatible. When I had Jaunty, it always said "device not managed" under the network applet, and I couldn't get it to go from there. I've upgraded to Karmic, and would love to finally sort this out, because I've been making due with a crappy usb wireless card for far too long. 

Problem is, when I click the applet now, it doesn't even say the wireless device isn't managed, it just mentions wired networks (which is greyed out because I don't have one). 

When I go to terminal and try ifconfig, I see eth0, which is the wired connection, but as far as I know, previously at least, the wireless should be ath0, and that doesn't show up at all. 

When I try lspci, for internet I have "00:0a.0 Ethernet controller nVidia Corporation MCP67 Ethernet". This is the wired connection again, I think, and the rest is about unrelated devices. 

I'm not sure where to start. Any ideas?

---

### Post by Omicron Machine on 2009-12-16
Self-bump. Sorry to do that, but I've put up with a lack of functioning wireless since I switched to Ubuntu. It should have been fixed about a year or two ago, it's the only recurring issue I have with Ubuntu, and I just want it to go away so I can finally enjoy my OS properly. But I'm just so profoundly, totally stuck. Halp?

---

### Post by HappyFeet on 2009-12-16
Did you try the driver from system>administration>hardware drivers?

---

### Post by Omicron Machine on 2009-12-16
Yep. The only one in there's for the video card.

---

### Post by hypergeek14 on 2009-12-16
I probably can't help you, but what does this spit out? 

```
sudo lshw -C network
```

---

### Post by Omicron Machine on 2009-12-16
It only gives anything for eth0, the wired connection.

---

### Post by hypergeek14 on 2009-12-16
Well I only know things about driver issues, so I'm stumped.  But I hope someone with more beans can help you.

---

### Post by Omicron Machine on 2009-12-16
I sure hope so. Thanks anyways. :)

---

### Post by IcarusR on 2009-12-17
What type of card is this ?? USB, pcmcia ....

---

### Post by Omicron Machine on 2009-12-17
The USB one I've been making due with actually worked out of the box with no need to install anything, now that I think of it. The "real" one is just a regular laptop wireless card (PCI?), as far as I know. I should have written down the exact model while I was looking at it. Maybe I should go back in and get that info so we at least know for sure?

---

### Post by Omicron Machine on 2009-12-21
Maybe not so much a bump as a gentle push.

---

### Post by Omicron Machine on 2009-12-25
C'mon, guys, I really, really **need** this fixed. I've had it up to here with the stupid USB wireless card. The darn thing is sticking out of the side of the laptop all the time; it gets hit, crunched, caught on things, because a laptop is inherently mobile. Sometimes the USB card gets caught on something and just plain snaps of completely and has to be replaced. Over a year or two, I've had to replace it several times now for various reasons, and there's just no reason I should need it at all. The reception for the signal and the speeds are vastly inferior to a real card. This is getting inconvenient, inefficient, annoying and extremely expensive. Don't get me wrong here, I love computers, and I love Linux, but this problem is actually making me truly, really and sincerely **hate** this machine and everything associated with it. At this point, I need this resolved badly enough I'm willing to just throw money at it until it's fixed. I am willing at this point to pay someone, somewhere, somehow to just fix the thing so I can actually use it properly for just once in the >1 year I've had it. I can't fix this myself, I wish I could, but I can't, and if no one here has any more suggestions or ideas, can you at least suggest places that might fix it for money?

---

### Post by Fir3chi3f on 2009-12-25
Do you know what kind of wireless card you have? What version of ubuntu are you running?

---

### Post by Omicron Machine on 2009-12-25
The version of Ubuntu would be Karmic, an upgrade from Jaunty (where this didn't work either, or in Intrepid or Hardy) that otherwise seems to work just fine. 

The "real" card, I just had to open up the back of the laptop and look since the system can't see it and won't tell me. Apparently, this isn't an nvidia anything, it's Intel. Sorry about that, I'll be appending to the OP about that. Anyways, the wireless card I apparently put in there (it was a rather long time ago) was labelled "Intel PRO/Wireless 3945ABG Network Connection", with the model number "WM3945ABG".

---

### Post by Fir3chi3f on 2009-12-25
As I've just posted in another thread, if you could try this real quick:
```
sudo apt-get install linux-backports-modules-karmic
```

and if that doesn't work, a more extreme fix would be:
[http://ubuntuforums.org/showthread.php?t=1309072](http://ubuntuforums.org/showthread.php?t=1309072)
(you don't need to install wicd)

---

