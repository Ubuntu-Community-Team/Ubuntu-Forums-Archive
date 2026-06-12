---
title: "tc1000: wlan no wpa in networkmanager dropdownlist and pen driver"
date: 2008-07-13
forum: Hardware
---

### Post by n00bThatNeedsHelp on 2008-07-13
Hi all,

I just installed xubuntu (8.04) on my tc1000 (compaq tablet pc).
It all works fine except 2 things.

When I click on the network icon in the right above corner I get a list of wifi ap's, when I try connect to my router I only get some wep security in the dropdownlist, while my router uses wpa/wpa2 security.
Without security is works fine and in XP it works fine on wpa.
The wlan controller is the: Atmel at76c506 802.11b.

Second I got the pen to move the mouse with.
This does'nt work at all.
I tried this one: [http://linux-tablet-pc.dhs.org/#Pen](http://linux-tablet-pc.dhs.org/#Pen)
but the make ; su -c make install, does'nt work at all.
I tried make.
I tried su -c make install, which gives me the error unknown id: install/

I have no clue what so ever.
I really hope you can help me.
(btw. I tried ubuntu and its very slow in the tablet pc and wlan and the pen does'nt work in ubuntu either)

I'm not very known with Linux so if you are trying to help me please act like I'm a retard.

---

### Post by walkerk on 2008-07-13
whats the output of
```
aptitude show wpasupplicant
```

---

### Post by n00bThatNeedsHelp on 2008-07-13
A whole bunch but state shows installed, if thats what you were looking for.

---

### Post by n00bThatNeedsHelp on 2008-07-13
I just found this: [http://packages.ubuntu.com/hardy/net/atmel-firmware](http://packages.ubuntu.com/hardy/net/atmel-firmware)

Just installed it and it does'nt seem to help...

---

### Post by n00bThatNeedsHelp on 2008-07-14
Today I found this: [http://ubuntuforums.org/showthread.php?t=202834](http://ubuntuforums.org/showthread.php?t=202834)

And still it does'nt work :(

Does anyone has any suggestions?

---

### Post by joeinbend on 2008-12-07
I know this is an old post, but I thought I'd chime in. I also have a Compaq TC1000 tablet that I've been dabbling with getting Ubuntu installed on over the past few weeks.

Regarding the Wi-Fi issue, this is not a driver issue. the problem is, the TC1000 has the older 802.11b hardware (11Mb/sec), not the now commonly-used 802.11g (54Mb/sec) hardware. WPA security is not supported by the 802.11b revision, it will only support the older WEP security methods.

I ran into this issue on mine as well, and for me I just turned off all security on my wireless network, because I live on a 4 acre ranch where no one has physical range to my network, so security isnt an issue! I realize this is not the norm; I would recommend just rolling your network back to WEP encryption and also use MAC filtering, which although this is nowhere near as robust as WPA, it still will stop all but the most persistent attacks.

The other option would be to get another (cheap!) access point, put it on your DMZ with either no security, or the older security mentioned above, that way your internal network would be protected by your router. You can then just use this access point for your TC1000 for internet access.

Just some ideas :)

---

### Post by hoki_goujons on 2009-01-11
If I can do another resurrection of this thread...

I've got a TC1000 that I'm trying Xubuntu 8.10 on, and having no luck connecting to my wifi. As above, there's no 'WPA' option to choose from.

I understand the point about it being a hardware problem, but I disagree - if it was a hardware problem then no OS would be able to connect to my network with it. As it is, XP can handle it with no problem at all. To my mind, this makes it a software problem. It's also the only thing stopping me from changing the TC1000 over to Xubuntu full time, as it's a hell of a  lot faster than with XP.

Is there really no way to make Linux work with my wireless on this? I'm not prepared to drop my router to WEP or buy more kit to put in a DMZ.

---

### Post by joeinbend on 2009-01-11
Hi Hoki,
Can you verify for sure that your access point is using WPA, and that the TC1000's 802.11b wi-fi is connecting to it? I would love to do the same, Unfortunately my TC1000 currently has no OS (it's between OS's at the moment... kind of like what you tell people instead of 'you dont have a girlfriend', you're between girlfriends...? ok, I digress... )

To my knowledge, the specs on 802.11b cannot handle the rotating key algorithm that WPA uses. If this is incorrect, I am all ears!

---

### Post by hoki_goujons on 2009-01-12
Hi Joe,
Yup, I'm looking at the router's settings now. It's set to use WPA-PSK and it's on 802.11b+g. Works fine on XP and it's never given me any indication that it's done something clever. In fact I'd never given it any thought until now. I wonder how it's doing it?

Xubuntu seemed to fly on the TC1000 btw - mine's only got 512mb of ram and XP gets very creaky on it.

---

### Post by joeinbend on 2009-01-12
I agree about the performance between XP and ubuntu on the TC1000. Not to hijack the thread, and perhaps we should start a new one, but have you successfully gotten all of the hardware drivers for the TC1000 working in Xubuntu? Pen driver, power management? I would love to revive my TC1000 if I know I can get it working 100% on Ubuntu!!!

---

### Post by dbharsh on 2009-11-23
An even later followup to this post; I recently acquired a TC1000 and was here investigating the possibility of running a Linux on it.  I did struggle with setting up the wireless while it was running XP for this same reason (no WPA) - and I found an updated XP driver which supports WPA on this hardware (see [http://h20000.www2.hp.com/bizsupport/TechSupport/SoftwareDescription.jsp?lang=en&cc=us&prodTypeId=0&prodSeriesId=307008&swItem=PSG_I19836-103447&prodNameId=307010&swEnvOID=1059&swLang=8&taskId=135&mode=4&idx=0](http://h20000.www2.hp.com/bizsupport/TechSupport/SoftwareDescription.jsp?lang=en&cc=us&prodTypeId=0&prodSeriesId=307008&swItem=PSG_I19836-103447&prodNameId=307010&swEnvOID=1059&swLang=8&taskId=135&mode=4&idx=0)).

So, while I'll be trying out some flavor of linux, I'll want to make sure I can find a linux driver for the wireless which also supports wpa.  

If either of the original two folks resolved the issue (WPA dropdown) it would be great to update this thread with the solution - and if I find one that works, I'll try to remember to post back...

---

### Post by hoki_goujons on 2009-11-25
I gave up in the end, sorry. I'm now running Karmic Koala on an Acer Aspire One and it's fantastic. Just works.

---

