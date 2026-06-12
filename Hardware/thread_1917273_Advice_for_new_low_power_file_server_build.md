---
title: "Advice for new low power file server build"
date: 2012-01-29
forum: Hardware
---

### Post by cruiserandmax on 2012-01-29
Looking for suggestions to build a very low power, <45watts total, Ubuntu server with gigabit LAN, and at least 2GB RAM, and two hard drives (non-raid).

For the past five years I've been running Ubuntu mainly as a home network file server and bit torrent client using this:

[http://www.newegg.com/Product/Product.aspx?Item=N82E16856167012](http://www.newegg.com/Product/Product.aspx?Item=N82E16856167012)

With a 1ghz Via C7 CPU, 1GB RAM, a 512GB HD, and a 1TB HD (no raid), the whole setup runs at about 35-40 watts under load. There is generally just enough free memory and horsepower for me to do basic web browsing and scripting while it does it's other duties, but it's a slug.

With my main concern being power consumption I want to upgrade to something that will support gigabit ethernet, use 2GB of RAM, and be slightly faster in the CPU department for the occasions where I actually use the machine directly for basic web browsing, scripting, whatever. Otherwise I'd like a similar form factor to what I have now, allowing for two hard drives (no raid).

It looks like the Cedar Trail Atom CPUs- D2700 or N2600, might be a good bet power-wise. I assume even the N2600 would also run the machine noticeably faster than my Via 1GHZ C7 CPU...? Motherboards based on these CPUs don't seem to widely available yet.

Thanks!!

---

### Post by oldfred on 2012-01-29
this thread started in 2009:

HOWTO: Build an energy-efficient Ubuntu box 
[http://ubuntuforums.org/showthread.php?t=1179877](http://ubuntuforums.org/showthread.php?t=1179877)

---

### Post by jmarcf on 2012-01-29
Why not just get a NAS device for around $200?. I have a QNAP that replaced a Linux file server and has been near perfect. 

Sorry Also they are low on power consumption. Mine uses less then 5watts when not under load and I think around 30watts under load.

---

### Post by ahallubuntu on 2012-01-29
> **jmarcf said:**
> Why not just get a NAS device for around $200?.

Probably for the "occasions where he actually uses the machine directly for basic web browsing, scripting, whatever."

---

### Post by ahallubuntu on 2012-01-29
> **cruiserandmax said:**
> Looking for suggestions to build a very low power, <45watts total, Ubuntu server with gigabit LAN, and at least 2GB RAM, and two hard drives (non-raid).

Out of curiosity, why do you need it to use under 45 watts under load?  It sounds like the server will be idle most of the time but you will occasionally use it as a remote desktop?

FYI, my buddy just built an i5 65 watt TDP-based system that he put on a watt meter - draws only 34 watts at idle he reports.  (No hard drives, just one SSD.)  This is with some generic Asus socket 1155 motherboard.  He uses it as a desktop computer too.  I'm sure that i5 jumps the power consumption when it's being used, but most of time it should be drawing close to 34 watts.

You can get a low-power i3 like this one that's only 35 watt TDP instead - that should use even less than 34 watts in a motherboard like my friend's but still be light years faster than what you've been using:

[http://www.newegg.com/Product/Product.aspx?Item=N82E16819115094](http://www.newegg.com/Product/Product.aspx?Item=N82E16819115094)

(No, probably not 30 watts less than the i5 at idle - maybe 10 watts less is my guess.)

Does this server have to be on 24/7, or can you wake it up only when you use it?  FYI, one of my Ubuntu servers at home is set to standby after an hour of inactivity, but I can wake it up from anywhere using Wake-On Lan (WOL) using my DD-WRT router.  It's remarkably reliable compared to an old Windows server that I never could make work well with WOL.  It's never not woken up when needed.

You could also have the server shut itself off at a set time every day and automatically resume once a day if that's easier for you.

What really matters in my opinion is total power consumption over a set time period, not immediate power consumption.  But I'm not sure what your exact constraints are.

---

### Post by cruiserandmax on 2012-01-29
First thanks for all the ideas!

> **ahallubuntu said:**
> Out of curiosity, why do you need it to use under 45 watts under load?

I don't really- that's just what my current system draws. Though "idle" my current system is ~20-25watts.

You are completely right in your suggestion to think about average draw over time. That's kind of why I was thinking Atom- the N2600 draws 3.5watts TDP, and it's technically a dual core 1.6ghz CPU. Though I don't really know how it would compare against the i3 (great suggestion btw) for stuff like web browsing. I'm really only looking for a slight improvement for speed in general use tasks over my current setup, but that is lowest on my priority compared to gigabit ethernet, and low power consumption over time.

The WOL thing is generally a really nice idea- I actually do that with my windows PC in the house so I can get into it from wherever on a rare occasion. But the linux server does need to be on 24x7 as it's pretty much always got torrents running, and a couple web services that I wouldn't want to have to wake the thing up to access all the time. Shutting down on a schedule for part of the night maybe a good idea though...

Thanks again for all of the thoughts- much appreciated.

---

### Post by cruiserandmax on 2012-01-29
> **oldfred said:**
> this thread started in 2009:

HOWTO: Build an energy-efficient Ubuntu box 
[http://ubuntuforums.org/showthread.php?t=1179877](http://ubuntuforums.org/showthread.php?t=1179877)

Thanks, there are lots of useful ideas in there for keeping total power consumption down. In this thread I'm really looking for specific advice about what current hardware would do the best to fit my scenario without lots of management of the machine. My current setup draws ~22watts just sitting close to idle all the time, and it's over five years old. So I was just thinking that without too much thought I could just replace a bunch of hardware and do about as good, but also get gigabit ethernet, and maybe a slightly faster desktop experience.

---

### Post by ahallubuntu on 2012-01-29
I built an Atom box back in 2009 to use as a 24/7 web server (using FreeBSD though - current uptime is 3+ years.).  It was also 1.6GHZ dual core + dual threaded (recognized as four logical cores in any OS).  It's fast enough for my web server, though my next build will be something faster.  Atom is not a great CPU for "desktop" stuff - it doesn't have the ability to "upshift" for performance the way the i3 does.  An i3 1.6GHZ dual core would be way faster than an Atom (but also consume more power).

But if you can live with the Atom being a bit slow for desktop stuff but power-efficient otherwise, it might be the way to go.

---

### Post by Jagoly on 2012-01-30
My own personal server isn't exactly what you wanted, but it is very similer.

Sandy Bridge i3 2100t (35w tdp)
2 WD scorpo blue 320gb Raid 1
ASRock H67M-ITX
Antec ISK 310-150 case, with a 150w PSU (80+ bronze I think, can't remember)
2gb Kingston Valueram ddr3

It was just over $500 not including shipping (bought in july). I've got it running a small website (apache), basic home file sharing, and (it's main use) a minecraft server. It does all of these things with ease. It's almost silent aswell, and fits on the kitchen bench under my router.

---

### Post by cruiserandmax on 2012-04-04
I just discovered this:

[http://www.via.com.tw/en/products/embedded/mserv/s2100/](http://www.via.com.tw/en/products/embedded/mserv/s2100/)

Possibly exactly what I'm looking for...

---

