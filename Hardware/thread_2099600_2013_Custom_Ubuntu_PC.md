---
title: "2013: Custom Ubuntu PC"
date: 2012-12-29
forum: Hardware
---

### Post by SlvrYeti on 2012-12-29
I'm planning on building a custom PC (my first since 2005/6). I've been using Ubuntu on and off for sometime but my current laptop has a few pieces of hardware on the incompatibility list.

Now Steam is on Linux and I can only see it going one way (spoiler: up) and I'm going to make Ubuntu my main OS on a custom rig I'm going to be building in the next week or so.

I have a couple of questions I'm hoping someone could answer please:

[LIST=1]
[*]How does Ubuntu handle SSDs?
[*]Is it worth me going with NVidia over ATI/AMD due to their recent Linux driver releases?
[*]Is there a 2.4Ghz/5Ghz Dual-Band Wifi card recommended?
[/LIST]

Thanks for reading.

---

### Post by 2F4U on 2012-12-30
> 
[LIST=1]
[*]How does Ubuntu handle SSDs?
[/LIST]


While Ubuntu works out of the box on SSD's, some tweaks are recommended:

[http://askubuntu.com/questions/19376/installing-ubuntu-on-a-ssd](http://askubuntu.com/questions/19376/installing-ubuntu-on-a-ssd)
[http://askubuntu.com/questions/1400/how-do-i-optimize-the-os-for-ssds](http://askubuntu.com/questions/1400/how-do-i-optimize-the-os-for-ssds)

> Is it worth me going with NVidia over ATI/AMD due to their recent Linux driver releases?

Difficult question. If you read through the forum, there are a lot of complaints about both nVidia and ATI proprietary drivers in Ubuntu 12.10.

---

### Post by SlvrYeti on 2012-12-30
Thank you for the reply 2F4U. I'm a little put off using an SSD from reading that. As for NV & ATI, I'll have a look through the forums.

---

### Post by The Spectre on 2012-12-30
> **SlvrYeti said:**
> I'm a little put off using an SSD from reading that.

You should be fine with using an SSD Drive.

I am currently using a OCZ Vertex 3 Max IOPS SSD and it works great. 

When I first started using SSD Drives I was Amazed at the speed difference.
It was the Biggest Performance Boost that I had ever seen from an upgrade.

The info that was in that first link is kind of dated it was referencing Ubuntu 10.10 and I would imagine that current versions of Ubuntu do a much better job with SSD's.

I would imagine that there can still be some Tweaking that can be done in Ubuntu just like there is in Windows to achieve Optimal Performance.

---

### Post by SlvrYeti on 2012-12-30
> **The Spectre said:**
> You should be fine with using an SSD Drive.

I am currently using a OCZ Vertex 3 Max IOPS SSD and it works great. 

When I first started using SSD Drives I was Amazed at the speed difference.
It was the Biggest Performance Boost that I had ever seen from an upgrade.

The info that was in that first link is kind of dated it was referencing Ubuntu 10.10 and I would imagine that current versions of Ubuntu do a much better job with SSD's.

I would imagine that there can still be some Tweaking that can be done in Ubuntu just like there is in Windows to achieve Optimal Performance.

TRIM is one thing if that isn't automatically enabled. It's going to be a pain picking Ubuntu/Linux compatible parts I feel.

---

### Post by rg4w on 2012-12-30
> **SlvrYeti said:**
> It's going to be a pain picking Ubuntu/Linux compatible parts I feel.
Not so much.  The kernel is pretty good these days with most hardware, so while it's possible to run across mobos with exotic components most have worked well out of the box for me.

I've found it helpful to read the comments at NewEgg for folks who've used a particular model with Ubuntu or other Linux.

If you don't find the info you're looking for there, post the mobo here and chances are someone else has already tried it out and can offer feedback.

---

### Post by The Spectre on 2012-12-30
> **SlvrYeti said:**
> It's going to be a pain picking Ubuntu/Linux compatible parts I feel.

> **rg4w said:**
> Not so much.  The kernel is pretty good these days with most hardware, so while it's possible to run across mobos with exotic components most have worked well out of the box for me.

I've found it helpful to read the comments at NewEgg for folks who've used a particular model with Ubuntu or other Linux.

If you don't find the info you're looking for there, post the mobo here and chances are someone else has already tried it out and can offer feedback.

I agree you should have little if any problem with most of the hardware that is out there.
 
Most of the hardware will be handled by the Linux Kernel and the instillation of Drivers will be unnecessary.

And to improve Hardware support you could just update the Linux Kernel...
[http://kernelnewbies.org/Linux_3.5_DriverArch](http://kernelnewbies.org/Linux_3.5_DriverArch)

[http://kernelnewbies.org/Linux_3.6_DriverArch](http://kernelnewbies.org/Linux_3.6_DriverArch)

[http://kernelnewbies.org/Linux_3.7_DriverArch](http://kernelnewbies.org/Linux_3.7_DriverArch)

The only Driver that I had to install was for a Samsung Color Laser Printer and that was only to improve the printing of Pictures. It was recognized right away by Ubuntu 12.10 but it printed very dark so in this case installing the Driver was necessary.

---

### Post by DisturbedDragon on 2012-12-30
SSD's work great out of the box under Ubuntu and many Linux distro's.  I use Samsung SSD's on my Mint 13 and 14 machines. TRIM is activated automatically.

I use Ubuntu and derivatives on many machines with many different chipsets.  No issues with any nVidia, AMD or Intel chipset save some of the Intel HDA audio chipsets.  There are workarounds and fixes though.  

nVidia fake RAID works well, hardware RAID cards work as long as the manufacturer has Linux drivers, though I would stay away from RocketRAID cards.  I have personally had some serious problems with their horrible drivers.

nVidia and ATI cards work quite well with current kernels and releases.  I utilize nVidia 460GTX, 9600GT in SLI, 9800GT, 7025/7050 with brilliant results.  ATI HD6310 works on my HTPC, thou I had issues with the HDMI at first. ATI 57xx cards work quite well.   ATI drivers still have issues with Linux although not nearly as bad as their Windows counterparts.

Just to be safe, check compatibility of any exotic hardware you are considering.

---

### Post by SlvrYeti on 2012-12-30
Thank you for all the replies. The GPU would most likely be an ATI 7970 or NVidia GTX 670 or 680. I've yet to decide.

The one thing that concerns me is that most Intel CPUs now have graphics on-chip. My laptop currently has one with a discreet ATI 6XXX GPU and it isn't possible to switch. I have to disable the ATI card in Ubuntu so I'm stuck with the on-chip GPU which doesn't suffice for games.

I'm doing a lot of reading on parts so any replies are welcome and gratefully read.

---

### Post by SlvrYeti on 2012-12-30
A small update for the purpose of this thread, I've done some searching and found the [TP-Link Wireless N Dual Band PCI Express Adapter (TL-WDN4800)]("http://www.tplink.com/en/products/details/?model=TL-WDN4800"). I found a user on Google+ praising the card and that it works like a dream with the ath9k drivers in Linux.

It's only £28/$45 so this is the card I'll be going with.

---

