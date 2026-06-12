---
title: "Averatec 6130-HS information..."
date: 2006-02-13
forum: Hardware &amp; Laptops
---

### Post by DarkED on 2006-02-13
This is not a question, it's an answer. Here I'm gonna tell you what devices Ubuntu will detect, and which devices it wont. I would read this BEFORE you install Ubuntu on your 6130.

Okay, the Averatec 6130-HS laptop has the following standard hardware:

Pentium 4 w/ HT @ 3000mhz
512meg DDR
60gig HDD
ATi Mobility Radeon 9600/9700 64meg
Ralink wireless card
SmartLink 56k v.92 modem (it's a winmodem)
SiS Ethernet 10/100
SiS Sl7012 soundcard w/ SPDIF 5.1 output
15" LCD-XVGA widescreen @ 1280x800 optimal res

Okay, so what will Ubuntu detect and configure on install? Everything ... except the SL modem. However, not all devices are configured correctly.

SmartLink 56k modem: Well, it's a winmodem, so that means its basically a driver that uses a chip instead of a 'real' 56k modem. The official drivers from [www.smlink.com](www.smlink.com) didn't work for me, but they may work for you. If nothing else, it's worth a try. I use wireless internet so I'm okay without this...

The ATi card: Everyone knows that ATi has had some small problems in Linux because of a lack of good drivers. The user-made drivers are very good because the people that made them worked very hard to bring you full graphics support, however, they aren't as good as a proprietary driver in Windoze. But never fear, ATi has FINALLY come to the rescue, and released 'official' drivers for the 8800 series (I think) and up. If you have a 6130-HS,  that means you :D You can read an excellent how-to by mlomker here: [http://ubuntuforums.org/showpost.php?p=423584](http://ubuntuforums.org/showpost.php?p=423584) - If you install the official drivers your ATi performance will be MUCH better!

The SiS Sl7012 - Getting XMMS to play: By default, XMMS will not play on this soundcard - it will give you the "Check three things" error. The way to make it play is to go into XMMS preferences and go to plugins, make sure the input plugin is whatever file you are playing, and make sure the output plugin is the latest ALSA. Click on 'config' with ALSA highlighted and make sure 'Device Settings' has the card selected (instead of 'Default Sound Device') - that should get you going! Keep in mind that XMMS never wants to save these settings for me...

That's the big stuff I have figured out, I'll add more as it comes!

---

### Post by DarkED on 2006-03-04
I said I would update, so here I am!

Three weeks in and Ubuntu is working great on this laptop. I haven't had any problems so far. After the inital hump with getting the ATi card to work right, everything is great. The dialup modem still doesn't work, but I can use Windows if I absolutely need it (which is never.)

So I'd like to say "Great choice" to anyone who decides to install Ubuntu on this laptop. If you need any help, don't be afraid to contact me!

---

