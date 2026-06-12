---
title: "Motherboard fried (?), need super cheap HTPC options..."
date: 2016-09-13
forum: Hardware
---

### Post by mma8x on 2016-09-13
Got this barebones PC 4 years ago to use as an HTPC. HDD went out a couple of months ago, and I FINALLY got mythtv installed and working again. About 3 days later, the computer turned off, never to turn on again. Guessing the MB is fried. It has an integrated 19v input. I tried a new brick, but it didn't work either. This PC was fine for my needs, and I need about the same power. I would love to just swap in a new MB, but that is proving difficult. It doesn't look like this is a standard/common form factor, and I'd like to use a dc power supply. I got the barebones system for <$100 4 years ago, but can't seem to find a solution in that range now. I need room for the new 3.5" HDD. Options:
1) New barebones system (that can use my DDR3 1066 RAM)
2) New MB/MB+CPU (that can use my RAM and power supply)
3) ?

---

### Post by TheFu on 2016-09-14
HTPC can mean lots of things.  For many, it is just playback and access to internet streams.

Do you have a tuner?  It is installed or networked? I like the networked tuners best, since it means my recording OS can run inside a VM.

A r-pi v2 will playback most common content for about $55. Don't know about connecting to Myth. I use Plex on a different server and run Kodi+plexbmc on the r-pi for viewing.

If you need to record TV and transcode, then something like a Pentium G3258 is what I'd deploy. It was an amazing CPU for the price about 2 yrs ago. I picked up a $99 deal for that CPU + MB.  Things change, so it might not be the deal it was anymore. Shoved it into an existing case, reused a PSU, RAM, and HDDs.  It replaced an AMD E350 system which couldn't handle 1080p video.  It uses a normal ATX power. The stock cooling is sufficient to OC by 1Ghz (I don't OC).  

There might be better CPUs available today, so look for the price/performance you need. [https://www.cpubenchmark.net/cpu_value_available.html](https://www.cpubenchmark.net/cpu_value_available.html) might help. I've stayed with intel CPUs for a few years to get their integrated graphics, which work really well for video playback. They are making progress with Linux to have GPU-based transcoding.

---

### Post by mma8x on 2016-09-14
Thanks, that chart is great. So confusing when you shop every few years. I miss the 486 days where >clock speed = faster chip, end of story. I think I'm going to get a miniITX mobo/cpu combo, and a picopsu. Cheaper/quieter than an ATX supply. Should be able to do this for <$50. This machine functions as a back end server for storage of vids and DVR. Use an HD Homerun as a tuner.  No problems streaming 1080p on it before.

---

### Post by TheFu on 2016-09-14
You don't need to sell me on picoPSUs!  Been a user for years when silence is necessary.  Have an 80W version.

For back end storage, my G3258 rocks.  It runs Plex, Calibre, NFSd, VPN, a few other services I don't recall, and has about 24TB of connected storage. ;)  The CPU doesn't really get that involved with pushing bits, but for transcoding video to the format needed by a Chromecast (POC device), it is nice to have the headroom.  Multiple GigE NICs to connect to different networks. Plus the G3258 supports VT-x, so running VMs is an option, thought I don't do that on it. Not bad for a $49 CPU!  Was looking for an 1150 socket upgrade today (your post got me thinking) ... and didn't find any compelling upgrade for around 3x the price.

I do have an older Core i5 (1st gen) that really needs an upgrade for all the things it does.  Need to stay DDR3 and need at least 6 SATA ports ... though a supermicro SAS card with support for 16 devices would be nice. ;)  That machine runs about 10 VMs, but does get bogged down during nightly backups to USB3 storage.  Something about USB just doesn't work well on that machine.  

Zero issues with USB on the G3258 box. Getting amazing USB3 storage and 920+Mbps network performance on it.

---

### Post by mma8x on 2016-09-22
Ok, so I ended up going with [this]("http://www.ecs.com.tw/ECSWebSite/Product/Product_Detail.aspx?DetailID=1564&CategoryID=1&DetailName=Feature&MenuID=17&LanID=0") motherboard/CPU, a PicoPSU, and[ this]("http://www.newegg.com/Product/Product.aspx?Item=N82E16820231266") is the memory that I had. I think this should all be compatible, but when I power on, I'm getting nothing on screen. HDD spins up, lights go on, but no video output. Reading reviews that this board is picky about memory--would I get a bios screen with incompatible memory, or does this sound like it could be the problem?

---

