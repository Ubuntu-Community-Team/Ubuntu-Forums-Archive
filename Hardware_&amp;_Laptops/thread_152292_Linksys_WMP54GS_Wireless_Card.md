---
title: "Linksys WMP54GS Wireless Card"
date: 2006-03-29
forum: Hardware &amp; Laptops
---

### Post by Schmung on 2006-03-29
Anyone successfully gotten this working under Breezy Badger or Dapper Drake? 

The WMP54G is on the list of compatible cards, but I can't se this one anywhere. As far as I can tell it's pretty much the same chipset but with minor tweaks.  Have so far been utterly unable to get it working in either version of Ubuntu or Kbuntu. Have tried x64 builds of ubuntu and the x86 builds of kbuntu with no luck either way using ndiswrapper or otherwise.

I'm pretty much a total nub when using Linux - but aside from the cards point blank refusal to work I'm at something of a loss. Works just fine in Windows and my signal is ok, but the card never seems to even activate under linux.  I assume there is something reasonably obvious I'm missing, but not sure what it is yet. The searching I have done suggests that the 64 bit builds might have trouble with ndiswrapper, but the x86 builds I've tried don't seem to like my PC much and have crashed a fair bit.

I spent most of last night installing various builds and continually wiping the partition I've got Linux on in an effort to get it working, but to no avail. 

Any help is muchly appreciated.

Edit : Wasn't entirely sure where to post this as this concerns hardware and both currentish versions of Ubuntu so this seemed like the best place and I'm assuming the mdos wouldn't be too happy with having what is essentially a duplicate thread in both sections.

---

### Post by chrisjs162216 on 2006-03-30
Yup, it does work.  Here's a copy from the ndiswrapper list:
 Card: Linksys #[WMP54GS] Wireless-G PCI Adapter with Speedbooster -- [link here|List#WMP54GS] 
Chipset: Broadcom Corporation BCM94306 802.11g (rev 03) 
pciid: 14e4:4320 
Driver: Linksys [ftp://ftp.linksys.com/pub/network/WMP54GS_20050406.exe](ftp://ftp.linksys.com/pub/network/WMP54GS_20050406.exe) (new version) 
Other: Ndiswrapper 0.11 and 0.12. Works fine with 64-bit WEP key and WPA supplicant (Fedora core-2, Kernel 2.6.8 and 2.6.9). Use WMP54GS.inf 

If you are lost on how to install it, this tutorial should help: [http://www.hammett.cwhnetworks.com/joomla/index.php?option=com_content&task=view&id=13&Itemid=28](http://www.hammett.cwhnetworks.com/joomla/index.php?option=com_content&task=view&id=13&Itemid=28)

---

### Post by Schmung on 2006-03-31
Cheers for that, haven't seen that guide tonight. Now I just have to work out an alternate way of viewing it now that kubuntu seems to hate my USB flash drive. Joy.

---

### Post by javaJake on 2006-04-12
Ubuntu 6 Flight 6 will not accept this card!

---

### Post by chrisjs162216 on 2006-04-15
I had tryed Flight 6 after I messed up apt-get on Breezy.  Ndiswrapper-utils didn't work.  I don't *think* it's Dapper itself, but a 'bad' version on ndiswrapper-utils.  I had gone back to Breezy, but saved the Dapper version of ndiswrapper, and same think happened.  In other words, it's *possible* it'll work if you have the breezy version of ndiswrapper.   I tryed it, but I didn't spend much time on it, so it didn't work.  If you have Dapper installed, give it a try

---

### Post by javaJake on 2006-04-17
OK, just got it to work. The key is to...

1. Place this script in /usr/bin: (thanks troublemaker for this wonderful script!)
```

#!/bin/bash
ifconfig MYINTERFACE up
if [ `iwlist scan 2> /dev/null | grep MYESSID | wc -l` -ge 1 ]
then
	myEssid="MYESSID"
else
	myEssid="any"
fi
myInterface="MYINTERFACE"

iwconfig $myInterface essid $myEssid
iwconfig $myInterface rate 11M

```
2. Replace "MYESSID" with whatever the name of your network is.
3. Replace "MYINTERFACE" with whatever your wireless card's interface is.
4. Place this extra line right in front of the "iface" line in the /etc/network/interfaces file:
```

pre-up /usr/bin/bcm43

```
(Obviously, you should replace "/usr/bin/bcm43" with the name of your script you saved above.)
5. Restart your computer.

Your internet should be up right at boot!
I assume you've installed bcm43xx-fwcutter. This won't work with ndiswrapper, I don't think.

---

### Post by alterationx10 on 2006-04-29
I have a suggestion for the WMP54GS.
I am using that card, and have been having trouble with it as well. NDISWrapper works, it would only seem to connect to my router at random for some reason. Well, today I discovered that **removing the antennae** increases the signal for some reason.. Maybe it picks up too much interference from the rest of my electronics... Regardless, it seems to connect most of the time with it removed, and I tested it when downloading. After connecting to the router witout it attached, I put it back on and installed a package. It was going at 36 kb/s, I removed it and it ramped up to 160/200+ kb/s. Reattached it-- 36 kb/s again, took it off: went back up.

I've been switching from linux to windows for about a year because I could never get my wireless card to work right. Aparrently, it was as simple as removing the antennea ](*,)

---

### Post by blackdahliamurder on 2006-07-27
Any way we could get a new link? That link seems to be dead.

I also have a Linksys WMP54GS which works fine in the Knoppix live CD. I got ndiswrapper to work under Kubuntu, but I can't seem to set me network key.

Thanks.

---

### Post by javaJake on 2006-07-27
> **blackdahliamurder said:**
> Any way we could get a new link? That link seems to be dead.

I also have a Linksys WMP54GS which works fine in the Knoppix live CD. I got ndiswrapper to work under Kubuntu, but I can't seem to set me network key.

Thanks.

If you mean this link ( [http://www.hammett.cwhnetworks.com/joomla/index.php?option=com_content&task=view&id=13&Itemid=28](http://www.hammett.cwhnetworks.com/joomla/index.php?option=com_content&task=view&id=13&Itemid=28) ), then no. The domain hammett.cwhnetworks.com no longer works, so I assume that the website is down for good.

Fortunately, I am working actively on the same problem as you are. My topic is posted here:
[http://ubuntuforums.org/showthread.php?t=216031](http://ubuntuforums.org/showthread.php?t=216031)

I think I have found the answer. If it works (or doesn't) I'll post it later today. If it works completely, I'll repost all the steps I went through to get it to work, leaving out the parts that didn't work of course.

Hopefully we can find an answer to this mess. :p

---

### Post by javaJake on 2006-07-28
> **javaJake said:**
> If you mean this link ( [http://www.hammett.cwhnetworks.com/joomla/index.php?option=com_content&task=view&id=13&Itemid=28](http://www.hammett.cwhnetworks.com/joomla/index.php?option=com_content&task=view&id=13&Itemid=28) ), then no. The domain hammett.cwhnetworks.com no longer works, so I assume that the website is down for good.

Fortunately, I am working actively on the same problem as you are. My topic is posted here:
[http://ubuntuforums.org/showthread.php?t=216031](http://ubuntuforums.org/showthread.php?t=216031)

I think I have found the answer. If it works (or doesn't) I'll post it later today. If it works completely, I'll repost all the steps I went through to get it to work, leaving out the parts that didn't work of course.

Hopefully we can find an answer to this mess. :p

Aherm... ignore... I was talking about W**USB**54GS. Whoops.

---

