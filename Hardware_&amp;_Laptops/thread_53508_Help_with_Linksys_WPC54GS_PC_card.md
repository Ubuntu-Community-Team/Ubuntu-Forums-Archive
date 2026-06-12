---
title: "Help with Linksys WPC54GS PC card"
date: 2005-08-01
forum: Hardware &amp; Laptops
---

### Post by timelord726 on 2005-08-01
Hello everyone.  I just got a new laptop (well, not exactly new, but new for me).  It's an IBM ThinkPad T22.  I've been using Windows on this laptop during its entire time with me so far, but it is now time, as with all my other computers, to put Linux on it.  I was able to install Linux well enough, and I got everything working pretty much right away, except for my wireless card.  The wireless card I have for this laptop is a Linksys WPC54GS card.  I have searched these forums and noted that other people have had similar problems getting their cards to work.  One person, I note, even had the same laptop as me.  However, the solutions posted there are either too difficult for me to understand, or there is some kind of problem preventing their completion (i.e. no internet access).

If someone could help me get **ndiswrapper** working, which seems to be the best way to fix it, I would greatly appreciate it.

Thanks very much!

---

### Post by alastair lewis on 2005-08-01
I think your card has a broadcom chipset which can be a bit of a bind.
The relevent HOWTO is here ([http://www.ubuntuforums.org/showthread.php?t=25683](http://www.ubuntuforums.org/showthread.php?t=25683))

Is this right and how far have you got. If you have installed ndiswrapper and wireless tools you are pretty much there. Once the cards lights come on the final setup is straight foward.

---

### Post by timelord726 on 2005-08-01
[QUOTE=alastair lewis]I think your card has a broadcom chipset which can be a bit of a bind.
The relevent HOWTO is here ([http://www.ubuntuforums.org/showthread.php?t=25683](http://www.ubuntuforums.org/showthread.php?t=25683))

Is this right and how far have you got. If you have installed ndiswrapper and wireless tools you are pretty much there. Once the cards lights come on the final setup is straight foward.[/QUOTE]
 The card does light up, the power light but not the activity light.  I cannot install anything on the laptop that is not preinstalled due to the fact that I have no internet.  I would like to install ndiswrapper-tools, I believe, but I'm not sure how without internet.

---

### Post by alastair lewis on 2005-08-06
Wireless-tools comes with Ubuntu. You need ndiswrapper-utils. At 24k you should be able to grab the .deb file at work/kiosk/friends house etc.
It's at [COLOR=Blue]packages.debian.org/unstable/misc/ndiswrapper-utils[/COLOR]

Install with dpkg -i

Turn off WEP/WPA until you have got the card configured.

---

