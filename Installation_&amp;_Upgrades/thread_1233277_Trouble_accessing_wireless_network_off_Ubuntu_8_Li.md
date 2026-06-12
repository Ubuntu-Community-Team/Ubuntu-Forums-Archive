---
title: "Trouble accessing wireless network off Ubuntu 8 Live CD"
date: 2009-08-06
forum: Installation &amp; Upgrades
---

### Post by growthmetal on 2009-08-06
The wireless network is hosted from a Macbook Pro using its Internet Sharing option.  I'm able to access it from another Mac laptop, so I don't think the problem is on the network side.

When I boot Ubuntu 8 off its live cd I get no indication that there is any wireless network in the area at all.  When I go to Network Settings, under the Connections tab, both "Wired connection" and "Point to point connection" are gray.  Viewing their properties doesn't provide any field where I could enter the name of a wireless network.

When I right-click on the network icon in the taskbar, Enable Networking is checked.  When I right-click on that icon and choose Edit Wireless Networks, I get some controls for filling out information about a network, but all of them except the Name field are either gray or beep when I try to type in them.

I'm using a Compaq Presario CQ60.   Using Windows Vista on the same laptop, I've managed to connect to this particular wireless network when I turn its WEP encryption off.  When I turn WEP encryption back on it stops working.  Ubuntu doesn't even acknowledge the network's existence.

This thread on Apple's Support forums confirms my experience with Windows Vista:
[http://discussions.apple.com/thread.jspa?threadID=574499](http://discussions.apple.com/thread.jspa?threadID=574499)

This blog post explains how someone managed to do what I've been trying to do.  I did what he did with no success:
[http://blog.braceta.com/mac-os-x-airport-internet-sharing-with-ubuntu-with-wep/](http://blog.braceta.com/mac-os-x-airport-internet-sharing-with-ubuntu-with-wep/)

Thanks for any help.  I hope my description of the problem was comprehensive without being tedious.  :P

---

### Post by running_rabbit07 on 2009-08-06
From what I have read before you pretty much have to install Ubuntu in order to install the necessary drivers for the wireless card you are using.  You may also want to download and use the Ubuntu 9.04 Live CD for newer capabilities. If you install via Wubi, you will be able to test Ubuntu with better results.

To get better help as to how to get the wireless to work with out installing, please tell us which Ubuntu version you are using, 8.04 or 8.10 and which wireless card your laptop has installed.

---

### Post by KyleRickards on 2009-08-06
Oddly, if I boot with Live CD, wireless works. If I use a USB install created from within the Live CD, it doesn't. 

Kyle

---

### Post by running_rabbit07 on 2009-08-06
> **KyleRickards said:**
> Oddly, if I boot with Live CD, wireless works. If I use a USB install created from within the Live CD, it doesn't. 

Kyle

Doesn't really help the OP though. Different systems have different result which is why I threw out there for the OP to post more details. 

I personally don't use wireless because it is too slow, I have a 1000BaseT switch and wireless has nowhere near that capability.

---

### Post by growthmetal on 2009-08-06
My live cd is Ubuntu 8.04.  I don't want to wait 6 weeks to get a new one.  I'm installing Wubi with Ubuntu 9.04 right now.  My wireless card seems to be called "Atheros AR5007 802.11b/g WiFi Adapter".

Thanks for your help.

---

### Post by running_rabbit07 on 2009-08-06
> **growthmetal said:**
> My live cd is Ubuntu 8.04.  I don't want to wait 6 weeks to get a new one.  I'm installing Wubi with Ubuntu 9.04 right now.  My wireless card seems to be called "Atheros AR5007 802.11b/g WiFi Adapter".

Thanks for your help.

That's great. If you have any problems with Wubi you may want to start a new thread with Wubi in the title to the help you need from people who know more about Wubi. 

I used it for a short period of time and loved it so much I had force Windows tp live in a really small partition while allowing Linux to run free.

---

### Post by growthmetal on 2009-08-06
No problems with Wubi so far except it seems like it'll take forever to install.  It says it's got 12 hours to go and 2 hours ago it said it would take 14.  This is normal, right?

---

### Post by running_rabbit07 on 2009-08-06
> **growthmetal said:**
> No problems with Wubi so far except it seems like it'll take forever to install.  It says it's got 12 hours to go and 2 hours ago it said it would take 14.  This is normal, right?

Depends on your connection speed.

---

### Post by growthmetal on 2009-08-06
I started a Wubi-related thread:

[http://ubuntuforums.org/showthread.php?p=7745039#post7745039](http://ubuntuforums.org/showthread.php?p=7745039#post7745039)

---

