---
title: "Asus Eee 1005ha vs. Dell Mini 10"
date: 2009-11-14
forum: Hardware
---

### Post by timmy_sprinkles on 2009-11-14
I'm the market for a netbook and I'm torn between the Asus Eee 1005ha and the Dell Mini 10 but I can't decide which to get. So I decided I should ask you wise and wonderful people. (Keep in mind I'm putting Ubuntu 9.10 netbook remix on it)

[Asus Eee 1005ha]("http://www.newegg.ca/Product/Product.aspx?Item=N82E16834220551")

[Dell Mini 10]("http://www1.ca.dell.com/ca/en/home/Laptops/laptop-inspiron-10/pd.aspx?refid=laptop-inspiron-10&s=dhs&cs=cadhs1&ref=lthp") (The one of the far left)

What would you guys recommend? Also, which has better driver support?

---

### Post by davidryderuk on 2009-11-14
Hi,
Just looking at the graphics cards, I've heard second hand that "intel GMA 500" performance is awful in Ubuntu 9.10 and plagued with problems.

[http://www.phoronix.com/scan.php?page=news_item&px=NzQzMg](http://www.phoronix.com/scan.php?page=news_item&px=NzQzMg)
[https://bugs.launchpad.net/netbook-remix/+bug/417804](https://bugs.launchpad.net/netbook-remix/+bug/417804)
[http://ubuntuforums.org/showthread.php?t=1229345&highlight=intel+gma500](http://ubuntuforums.org/showthread.php?t=1229345&highlight=intel+gma500)
[http://swiss.ubuntuforums.org/showthread.php?t=1253406](http://swiss.ubuntuforums.org/showthread.php?t=1253406)

On the other hand I'm running an eeepc 1000 with the "intel 945GM" graphics card which works great. So on that basis alone I would recommend the eeepc 1005ha computer or anything else that doesn't contain the "intel GMA 500" graphics card.

The link shown below describes the current comparability of a lot of netbooks on ubuntu which you might want to check out.

[https://wiki.ubuntu.com/HardwareSupport/Machines/Netbooks#Asus%20Eee%20PC%201005HA](https://wiki.ubuntu.com/HardwareSupport/Machines/Netbooks#Asus%20Eee%20PC%201005HA)

---

### Post by timmy_sprinkles on 2009-11-14
I didn't even know that the Intel GMA 500s had issues. Thanks for the tip. :)

---

### Post by movieman on 2009-11-14
Asus 1005HAB works almost perfectly with UNR 9.10, so I presume the 1005HA will too; no idea about the Dell.

The only real issues I've had so far:

1. Wireless sometimes goes away and won't come back until I reboot. XP does the same at times, so that may be a problem with my wireless router or the hardware rather than the Linux driver.
2. Some video files won't play properly, but that may be a generic codec problem rather than video or audio drivers.
3. KDE display is often corrupt -- e.g. parts of menus sometimes get overwritten by the desktop background -- but I don't care because I'm using the default Gnome UNR interface which works fine.

Plus it comes with the whole disk partitioned for Windows, so you'll need to shrink the XP partition to free up space unless you plan to wipe the disk.

Edit: Actually, I just noticed that the 1005HA link claims to have an N280 CPU rather than 270, so perhaps there are other hardware differences to the 1005HAB.

---

### Post by davidryderuk on 2009-11-14
> 1. Wireless sometimes goes away and won't come back until I reboot. XP does the same at times, so that may be a problem with my wireless router or the hardware rather than the Linux driver.

I was going to stick to graphics support, since I don't really know anything about wireless support. However I did find this bug on launchpad about the 1005ha's wireless driver. I'm not sure if it applies to the 1005hab's wireless driver as well though.

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/414560?comments=all](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/414560?comments=all)

There seem to be two possible ways of making the connection more stable. 

1. Install the "linux-backports-modules-wireless-karmic-generic" package from the backports repository.

2. Use the windows xp wireless driver with Ndiswrapper.

I've never had to resort to either method myself since my wireless has always worked well.

Edit:

> 2. Some video files won't play properly, but that may be a generic codec problem rather than video or audio drivers.

Have you tried vlc player? It sometimes does slightly better on particular videos.

---

### Post by movieman on 2009-11-14
That bug is probably the one, since it only seems to happen after resume from hibernation. I'm used a Windows laptop which takes more than five minutes to get to a usable desktop after I tell it to reboot, whereas this one boots fast enough that I don't really need hibernate anyway.

---

### Post by movieman on 2009-11-14
> **davidryderuk said:**
> Have you tried vlc player? It sometimes does slightly better on particular videos.

The particular file I was trying to play yesterday didn't work properly in VLC either, which is why I'm guessing it's some kind of codec issue.

---

### Post by movieman on 2009-11-15
Actually, the same video file plays fine after I copied it to the netbook's hard drive rather than playing over the wireless network via NFS; so it looks like that's a network issue too.

---

### Post by marcdutonkin on 2009-11-15
Hello, i have tried Karmic on a EeePC 1008HA which has the same hardware than the 1005ha. 

Even if all seems to run out of the box, i confirm that wireless/networking has problems. For instance, if you start to stream a video file shared via Samba, through you local network, the image will freeze after one minute, and then periodically freezes and restores.
With system monitoring, you can see that the transfer rate falls down to zero in a nearly periodic way. And unfortunately, the use of the "linux-backports-modules-wireless-karmic-generic" package coming from the backports repository does not solve the problem.

So with karmic, it seems that it actually remains only two ways to stream videos: either to use a wired connection, either to use Ndiswrapper. I have tried with success the first way. The second way should be tried because Windows XP doesn't suffer from the same deficiency, as i was able to stream a complete episod of Dr House (for instance).

---

### Post by davidryderuk on 2009-11-15
Hi,
I thought I should mention that the Dell mini 10**v**, unlike the Dell mini 10, doesn't have the "intel GMA 500" graphics chip, so it should probably work okay. Maybe that would be worth considering if the asus eee 1005ha has wireless problems.

---

### Post by jocheem67 on 2009-11-17
Well, I've been running UNR on my asus1005ha-h with nearly any probs. I can confirm on the wireless though, there's an annoyance of the connection dropping to 30 -40 % strength. However no connection-loss overhere.
I do find UNR pretty slow, might be an issue with the intel-driver or the need to perform some tweaks on xorg.conf.
Am running Arch now though.

---

