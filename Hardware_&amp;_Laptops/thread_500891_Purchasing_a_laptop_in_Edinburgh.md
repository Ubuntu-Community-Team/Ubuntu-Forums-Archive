---
title: "Purchasing a laptop in Edinburgh"
date: 2007-07-14
forum: Hardware &amp; Laptops
---

### Post by dabugas on 2007-07-14
Hello, 

I am moving to Edinburgh for studies this fall and intend to buy a laptop once I land. Can anyone recommend a local shop that is Linux friendly? If there is no such thing, can anyone recommend an online retailer that caters to the UK (with reasonable customer support for the hardware)?

All I'm looking for is for a machine that can run Ubuntu more-or-less out of the box, including the common stumbling block that is WiFi. I have been using Linux for a long time, and Ubuntu specifically for a couple of years, but I'm no techie. I can edit scripts and compile stuff , but I'd rather *not* have to recompile my kernel or build a lot of custom drivers.

I have had a brief look through the compatibility lists, but they seem fairly out-dated. Because of the move I have many other things to worry about and I was hoping if someone could at least point me in the right direction. And, before I get asked,  yes, I'm being lazy and trying to avoid the research and trial-and-error required :)

---

### Post by Jim Connachan on 2007-07-14
I purchased an Acer Travelmate 4233WLMi from Fife Computers,High St,Kinross 01577 861878 and he installed Ubuntu 7.04 on it and it has run perfectly with no problems. The owner Kevin Celetano gives an excellent after sales and is very knowledgeable about Linux. Kinross is on a direct bus route from Edinburgh.

---

### Post by ugm6hr on 2007-07-15
How much do you want to spend?  If you want to go online...

I got this a few months ago - it's a lot cheaper now (£300):
[http://www.ebuyer.com/UK/product/123115](http://www.ebuyer.com/UK/product/123115)

Almost everything works out of the box (once Restricted Drivers activated).  I used Xubuntu7.04, but nothing to suggest Ubuntu won't be OK.  Small problem with kernel update and sound (so I'm on 2.6.20-15 kernel). Also - wifi works better with Wicd than Network Manager (if you want WPA - otherwise Network Manager is fine). Unfortunately, card reader not working (yet - [https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.15/+bug/62995](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.15/+bug/62995)).

EDIT: Just to clarify - the sound issue with the kernel update is not because the sound card is unsupported. There must be some issue with the updated kernel - because recompiling alsa gets it working.  I just couldn't be bothered ([http://ubuntuforums.org/showthread.php?t=457011&page=2](http://ubuntuforums.org/showthread.php?t=457011&page=2))

---

### Post by dabugas on 2007-07-15
Thank you both for the input.

Fife Computers (btw, is [THIS]("http://www.fifecomputers.co.uk/") them?) seems a little far, but I will give them a call. Supporting local businesses is always good :)

As for the laptop ugm6hr mentioned... it seems to be in the price range I'm looking, i.e., dirt cheap. But the sort of kernel problems you mention is exactly what I was hoping to avoid. I don't want to update my kernel and suddenly find my system dysfunctional. I didn't know what WiCD was, so I looked it up and found some info [HERE]("https://wiki.ubuntu.com/MeetingLogs/openweekfeisty/xubuntu"), but the website seems to be down and there's no package in the repos.

From what I've read Acer laptops seem to be, after Dell, the most compatible, so they are certainly one of my choices.

Thanks again. :)

---

### Post by imdano on 2007-07-15
[http://wicd.sourceforge.net](http://wicd.sourceforge.net)

---

