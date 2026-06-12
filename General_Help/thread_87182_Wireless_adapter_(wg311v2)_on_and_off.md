---
title: "Wireless adapter (wg311v2) on and off"
date: 2005-11-07
forum: General Help
---

### Post by flipz on 2005-11-07
Hi everyone!
I just installed Ubuntu (5.10) last night because I have tried several other distros and always had problems. The biggest feature I was looking for was that I would like my Netgear wg311v2 wireless card (PCI) to work right away, and I had many people tell me Ubuntu could do this.

To my surprise, it actually did! It recognized it right away, and all works great. The problem is it seems to always disconnect. If I am browsing around, it seems to have no problem staying connected. But if I'm idle for as little as 10 mins I seem to get disconnected. At one point last night it took about 3 hrs of being idle before it stopped working.

I got disconnected at some point overnight last night, but then after trying to browse webpages this morning for about a minute, it reconnected and started working again.

Does anyone know what could be causing this? The way I know I'm disconnected is because webpages just stop loading. Some just load and load and load and never go anywhere, some will say access denied, and some will say request denied. If I reboot, all is back to normal. 

I followed these instructions from ndiswrapper's wiki regaurding ubuntu:
> 
#1 Install ndiswrapper-utils: System->Administration->Synaptic Package Manager. Search for ndiswrapper. Click on the box to install ndiswrapper-utils. Click Apply to install it. (If there are errors, perhaps try Reload to refresh package lists). Close it.
#2 Get the drivers and install them as described in Installation, under the "2. Install your windows driver" **In this step I got a warning saying the drivers were already installed**
#3 Test the interface. System-> Administration->Networking. Click on "wireless connection", go to Properties, set it up (enter the essid, set to DHCP). Click OK. Deactivate the wired interface, activate the wireless. Unplug your network cable just to make sure, and see if you can get to anywhere on the internet (Open Firefox from the blue globe and try google). If it works, great. If not, go to Remove a driver below.
#4 If it works, write configuration for modprobe (as root): "ndiswrapper -m"


My internet worked right out of install like I said, but when it first started dropping out like that is when I followed the above steps. But I'm still having the same problem.

Should I try uninstalling and reinstalling ndiswrapper and my driver?

Thanks in advance for any and all help!

-flipz

---

### Post by flipster on 2005-11-07
Are you sure the problem is the PCI card and Ubuntu, and not your wireless access point.  I have had problems with wireless access points that overheat and then drop connection to my computers.  Get another wireless computer and see if it can connect when your Ubuntu machines loses connection.  If it is universal to both machines then you might need to vent your access point better.

---

### Post by flipz on 2005-11-07
Thanks for the response flipster. :)

It's not the access point... I have 4 other computers in the house that get a 100% signal to it (including 1 other in this room). And my access point is in an empty room of the house all by itself, so no problem with ventilation. And I've gotten a 100% signal in windows on this comp for 1.5 years now.

I tried this fix from the wiki: [StaticDnsWithDhcp]("https://wiki.ubuntu.com/StaticDnsWithDhcp?") and when that didn't fix it, I completely turned off DHCP and just put in my static info. It is still disconnecting about twice an hour, but it regains the signal at least.

Any other ideas from anyone? Is there a way for me to check my signal strength? I don't know if it's actually losing the signal, or my card itself stops responding, or what. I read somewhere that if the transmit voltage (or was it receive voltage?) was too high, that could cause some problems. But I don't know how to edit that info. Nor do I remember where I saw it. :???: 

Thanks!
-flipz

---

### Post by lupine_nickt on 2005-11-07
You could always keep ping running in a terminal as a quick 'n dirty temporary kludge, I suppose... 

Open a terminal and run :- ping -i 60 [http://www.google.co.uk/](http://www.google.co.uk/) 

Which will send a ping packet to Google every 60 seconds, keeping network traffic flowing and (hopefully!) stopping it from disconnecting. 

(edit) If you're paying for bandwidth, that works out at:- 64 x 60 x 24 = 33.488 megabytes/year, so not exactly expensive (/edit) 

As to why it's doing it... maybe some sort of power management? TBH, I don't have a clue. I've always used USB dongles ;)

xF,

...Nick

---

### Post by flipz on 2005-11-07
Well... activity was keeping it alive, but it must have just been a coincidence.

I was just on it, walked away for 2 minutes, came back and it was dead. I tried for 6 mins of trying to go to different websites or signing on to gaim, and it just timed out.

Finally I rebooted and all was well.

:confused: Still hoping for an answer. Thanks in advance!

-flipz

edit: i am now running KWiFiManager with the statistics window open, so I will at least know if I have a signal or not at times when I can't get on the internet.

---

### Post by flipz on 2005-11-07
As I said in the last post, I've been using KWiFiManger to monitor my connection stats. 

I thought it was going to actually be a fix as my comp lasted the longest yet w/o disconnecting, but then it got disconnected. I checked out my stats window, and if anything it actually had a little mini spike up in singal strength, but not down.

I do have random dips where it goes to probably 60%, but they only last for a second, and none of them were happening when I just got disconnected. I had a full signal.

I was disconnected for about a minute (still had full signal, but couldn't browse webpages, and was disconnected from gaim) and then it reconnected.

Any ideas now?

-flipz

---

### Post by Eigil on 2005-12-22
Hi!

Is there still no solution to this problem? I seem to have the same issue, although with another wifi-card. It would be nice if anyone could help me out here.

Eigil

---

### Post by BananaBoat on 2005-12-25
I have the same problem with another card, nothing to do?

---

### Post by oscartheduck on 2005-12-25
One potential source of the problem is a heartbeat signal; I've had a windows/linux dual boot box that had no problems with windows recognising a heartbeat signal from my ISP, but linux just doesn't like it. 

Let's see... random thread mentioning it: [http://www.xtremepccentral.com/forums/showthread.php?threadid=7487](http://www.xtremepccentral.com/forums/showthread.php?threadid=7487)

It's used, as mentioned above, to see if you're still online; this might be why you're getting a signal spike immediately before it drops you. It asks "Are you there?" and for whatever reason, quite possibly that there's usually a firewall installed and turned on in linux by default (though I'm not sure about Ubuntu - I've been using it for about ten minutes) so there's  no response from your box. 

Try monitoring your ports with ethereal and seeing if you get traffic aimed at a specific port immediately before being dropped. If it's happening consistenly, you'll need to unblock it.

Or visit the grc.com shields up to see if you have a firewall up and running that's killing things.

Although, now I'm thinking about it, didn't you say you've got four computers running on the same connection? So you're running a router, which is managing your connection. So this isn't it, otherwise your router would be dropping the signal.

Hm. I'd start running ethereal either way, see if you can get some useful information.

---

### Post by BananaBoat on 2005-12-26
Ubuntu shouldn't have any firewall, I'll try with ethereal.

---

### Post by stock99 on 2006-06-01
i having the same problem too. But i did a little experiment and found that if drop for too long even dhclient command can't bring back the connection. But if it just drop (say you do ifdown) , then bring it right back it still ok. Not so sure why.  


Besides, is any other netgear card that has no hassle on ubuntu? I would rather just by a new card

---

### Post by billylh on 2006-12-11
i have the same problem with both wep and open connect.  wep was acting up so bad that i changed the ap to open with mac filtering and it still disconnects after about 10 minutes.

ubuntu 6.06 using wusb54g(v4) connecting to a netgear router.  

if someone finds something out, please let me know.

tia,
billy

---

