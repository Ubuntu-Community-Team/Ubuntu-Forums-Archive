---
title: "H/W recommendations - POWERFUL + SILENT"
date: 2011-12-05
forum: Hardware
---

### Post by vskatusa on 2011-12-05
Hi,

I would like to build a mythtv backend. I want this to be powerful enough to transcode OTA HD content as quickly as possible at the same time consume very little power (24/7 usage) and it need to be dead silent.

I am sure many of you would have built such a UBUNTU server and welcome recommendations. Open to off the shelf systems as well.

---

### Post by vskatusa on 2011-12-06
Anybody :(

---

### Post by typhoon_tip on 2011-12-06
24/7 ? Silent ? If budget is not an issue, go for Lenovo T420 with i7 processor and NVidia Optimus. It cost a fortune, but it will transcode just about anything and not utilize the entire CPU (very silent fan too).

---

### Post by banjobreath on 2011-12-06
I have similar requirements.  Scientific and engineering heavy single-threaded cpu use.  And I would love it to be quiet.  Thinking i5 or i7 in full tower case with large slow fans.
But what motherboard?  
I am going to need to alternately boot into both ubuntu 32 for general music and web, and debian 64 or centos 64 for the heavy lifting.  So I want 4 or more SATA ports, at least 1 of which would be SATA-3.
Probably start with 8Gig memory.
But what motherboard?  There are so many i5/i7 motherboards - I need to stay away from troublesome built-in video and ethernet, especially since I may need to occasionally boot into older distributions.  Should support 1666MHz DDR3 I guess.
Thanks for advice

---

### Post by vskatusa on 2011-12-07
I need a desktop setup! Laptop by design are not meant for 24 x 7!

Anybody please...I am sure somebody has such a setup! All I want is to duplicate the setup so that I do not get into ubuntu compatibility issues. Please help :(

---

### Post by typhoon_tip on 2011-12-07
> **vskatusa said:**
> Laptop by design are not meant for 24 x 7!

Well it depends ;) You mentioned powerful and silent, I cannot think of anything else. Go for that laptop or directly go for a Mac if silence is main issue.

---

### Post by vskatusa on 2011-12-07
Mac? I need PCI card for my tuners.....Kindly eloborate?

---

### Post by Jagoly on 2011-12-08
For power, get something around the level of an i7-2600s. Low power consumption and lots of threads for encoding.

For noise it's all in the case. You could look into something along the lines of the Fractal Define Mini. MSI are great for mobo's.

---

### Post by vskatusa on 2011-12-08
Jagoly, thx for the tip. I want the complete parts list (mobo, cpu, memory, etc) of a successful build so that I can duplicate the same!

---

### Post by Jagoly on 2011-12-09
It depends what you need. You haven't listed all of what it needs functionally. I would assume at least 3 hard drives in raid 5, whatever size you think you need. The things that may have compatibility issues with mythbuntu would be the motherboard (MSI and Intel mobo's will work great), In VERY rare cases the cpu (stick with a current gen intel and you'll be all good), and worst of all the TV tuner(s). That is where you will need to do a lot of research. I don't know any cards specifically, myself.

Just put together a list of what you think would suit, then post it here.

---

### Post by MoreOrLess on 2011-12-10
SPCR is a great resource:
PSU: [http://www.silentpcreview.com/Recommended_PSUs](http://www.silentpcreview.com/Recommended_PSUs)
Fans: You don't have to be picky if you're going to have mechanical storage. I use cheap Yate Loons running off 5V.
Mobo/CPU/RAM: These really shouldn't factor into noise, so take your pick. Newer intel stuff is generally more efficient right now.
Mechanical hard disks: These end up being the loudest part of the system if you have good heatsinks/fans, so check out SPCR's site to see what's good nowadays: [http://www.silentpcreview.com/article29-page2.html](http://www.silentpcreview.com/article29-page2.html)
GPU: Stock coolers aren't quiet, unless you get a low-end passively-cooled model (I have a RadeonHD 4550 with a Yate Loon blowing on the heatsink).

Note: If you want a lightly used (500GB) Samsung 502HI at a reasonable price, and you live in the U.S., I can hook you up.

---

### Post by vskatusa on 2011-12-10
Maybe I have not explained properly! I do have current setup MythTV backend with TV tuner and hard drive. 

I however discovered that this machine does not have enough Ump... to transcode OTA HD content. I want to build a UBUNTU compatible machine and over the years I have found that UBUNTU works very good on old hardware but picky on new hardware. 

I therefore want mobo + sandy bridge cpu + graphics card + memory EXACT specs of already build system. I do not want to burn my fingers in buying parts and finally paying the price for UBUNTU gotchas!

If anybody has a complete spec of recent build of sandy bridge cpu I would like to hear from them.

---

### Post by Jagoly on 2011-12-10
I've built two this year. One is running ubuntu server, for minecraft, apache and samba servers, and the other ubuntu 11.10 desktop edition. Both work pererectly with no ubuntu compatibility issues.

However, neither are an exact match to what you want.

If you need an exact parts list, it is very unlikely you will get one. As I said, the only ting that you will really run into compatibility issues are the tv tuner(s). For that, you can ask around here, in a more specialised topic.

For what I would get, though:

Mobo: MSI Z68MA-ED55
I have not used this one specifically, however I have used an MSI Z68A-GD55 and that works perfectly. This one uses all of the same chips as that so identical ubuntu compatibility.

CPU: i7-2600s
Probably overkill, but this will encode multiple video streams pretty much instantaneously. Low power so you can use the stock cooler, which for my 2100t and the 2500k, was wonderfully quite.. My server has an i3-2100t, and the desktop has a i5-2500k OC'd to 4.7ghz. Both are great and compatible chips.

Memory: for this, you will not need alot, 4 or even 2gb of generic 1333mhz DDR3 memory will be perfect. Such as the exelent Kingston valueram 2gb I have in my server.

Hard drive: if you already have the storage server, than a small HDD or even a 60gb SSD will suffice. I have never owned an SSD, but the corsair force series 3 seems good and well supported.

PSU: a good 430w fanless one. This system could easily run off of a 300w, but better safe than sorry. Seasonic do some good 80plus gold fanless ones.

Case: up to you. Soemthing mATX. My vote is for then Fractal Design define mini.

Tv tuners: never used one myself. Ask around the forums. This is were you will hit problems.

You are building this, so meet your requirements in a parts list, and post it here

---

