---
title: "Help Me Build a Linux Desktop!"
date: 2009-10-29
forum: Hardware
---

### Post by mDuo13 on 2009-10-29
Recently a hard drive on my main, 4-year-old rig died (it has 3 separate drives being used for different data) and I'm using this as an excuse to build a new desktop. But the last two times I built a computer and tried to put Linux on it, driver support for my hardware was pretty spotty and I ended up defaulting back to Windows XP. This time I'm determined to get it right and so I'm asking for advice here before I put my computer together.

After talking to a couple friends, the preliminary build for my computer looks like this:
[[SIZE=2]ASUS P6T LGA 1366 Intel X58 ATX Intel Motherboard[/SIZE]]("http://www.newegg.com/Product/Product.aspx?Item=N82E16813131359")[SIZE=2]
[/SIZE][Intel Core i7-920 Bloomfield 2.66GHz 4 x 256KB L2 Cache 8MB L3 Cache LGA 1366 130W Quad-Core Processor]("http://www.newegg.com/Product/Product.aspx?Item=N82E16819115202")
[CORSAIR XMS3 6GB (3 x 2GB) 240-Pin DDR3 SDRAM DDR3 1333 (PC3 10666) Desktop Memory Model TR3X6G1333C7 G]("http://www.newegg.com/Product/Product.aspx?Item=N82E16820145250")
[XFX HD-577A-ZNFC Radeon HD 5770 (Juniper XT) 1GB 128-bit GDDR5 PCI Express 2.0 x16 HDCP Ready CrossFire Supported Video Card]("http://www.newegg.com/Product/Product.aspx?Item=N82E16814150447")
[Intel X25-E Extreme SSDSA2SH032G1 2.5" 32GB SATA II SLC Internal Solid state disk]("http://www.newegg.com/Product/Product.aspx?Item=N82E16820167013") (System disk)
2x [SAMSUNG EcoGreen F2 HD154UI 1.5TB 32MB Cache SATA 3.0Gb/s 3.5" Internal Hard Drive]("http://www.newegg.com/Product/Product.aspx?Item=N82E16822152175") (Data disks in RAID1)
[LITE-ON Black 4X BD-ROM 8X DVD-ROM 32X CD-ROM SATA Internal 4X Blu-ray Reader Model iHOS104-06]("http://www.newegg.com/Product/Product.aspx?Item=N82E16827106325")

I intend mainly to use this computer for watching anime fansubs or blu-ray discs, some light gaming, web browsing/etc., perhaps some image editing. Most of all I want it to be up 24/7 and last me for years.

Does anyone have any reservations or recommendations about the hardware choices? I was also considering swapping out one of the Samsung disks for a same-size, same-price Western Digital just so I would have different models that are less likely to fail around the same time.

Furthermore,  I could use some tips on the proper OS setup, how to use the SSD as an OS drive. Obviously the swap partition goes on there and most of the filesystem is there, too, but should the /home/ directory be mounted on the 1.5TB RAID, or should I have the raid accessible elsewhere?

As for software, I'm a real minimalist, I don't like the default Gnome desktop or Xfce in Ubuntu. So far my favorite windowmanager in Linux is IceWM because it's so spartan,  efficient, and the keyboard shortcuts are so simple to set, but I don't like re-generating the menus every time I add new software. Right now my Windows box is running Litestep with a really minimalistic theme, no desktop icons or taskbar and a system tray near the top-right. I still right-click for a program menu once in a while but that's not normal operation.

For music players, so far Audacious seems like the best for me, again I want something minimalistic, anything that resembles Winamp 2.x is great (though unicode support is nice). 

IM is a pretty big sticking point, since I really dislike Pidgin's and Kopete's default UIs. I'm considering using Psi but I'd rather have actual AIM/ICQ/MSN/YIM rather than using transport contacts. I'm not above compiling Miranda IM with WINElib to see if that's more to my taste as Miranda has been my go-to love affair client on Windows for years.

Also wondering if anyone has experience using a WACOM Bamboo tablet, I'd like to run Photoshop (not GIMP) but I'm not sure if WINE is up to the task.

Finally, for the file manager, on Windows I'm using XYplorer because it's stable, has tabbed file browsing, and scriptable regex-based batch renaming. So far I haven't seen a file manager on Linux that can do this... though on the plus side, Linux has a terminal that's actually good. Totally open to recommendations here.

Anyway, that about covers it for now, I'll be checking back regularly over the next few days before I decide to buy the parts and probably afterwards as I actually go and set it up.

P.S. I'm expecting to use 64-bit Ubuntu but I'm not wedded to the idea, and have considered running something like Gentoo also.

---

### Post by cascade9 on 2009-10-29
For light gaming, a 5770 might be more than you need. As far as I know, because of driver issues nVidia is still a better choice. The 5xxx series ATI cards are still a bit too new IMO, if your going to get problems from a video card its more likely with a fresh release, older cards tend to have more of the bugs ironed out. If you want a card in that price range, a GTX 260 would be what I would get. 

The i7s are nice and fast, but they use more power and are less efficent than the core 2 duos. An 8400 to 8600 c2d (or even a core 2 quad 9550) would be better for 24/7 use. 

I would not mix and match drives in a RAID array. Personally, I would get 2x 1.5TB WD GP drives. I would also put /home on the SSD, and use the array for storage only. 

Photoshop no WINE should be good, provided you have the right version- 

[http://appdb.winehq.org/appview.php?appId=17](http://appdb.winehq.org/appview.php?appId=17)

---

### Post by mDuo13 on 2009-10-29
Thanks for the feedback!

Good news about Photoshop, I swear I always forget that WINE has a database of app compatibility. XD

I was told that the 5770 had good Linux drivers, got linked to a few articles about it on a site called Phoronix. But if the GTX 260 is more compatible, then I might consider something like this: 
[XFX GX260XADJC GeForce GTX 260 896MB 448-bit DDR3 PCI Express 2.0 x16 HDCP Ready SLI Supported Video Card]("http://www.newegg.com/Product/Product.aspx?Item=N82E16814150398"). 

As for the CPU, you raise a good point. Certainly the i7 uses more power than a Core2Duo. The problem is that it feels like a Core2Duo/Quad would be holding my machine back 3 or 4 years from now and the i7 would not. Maybe that's just the hype train, but it's also true about the Pentium 4 in my current computer. How much does the power consumption matter in the long run?

---

### Post by cascade9 on 2009-10-30
The ATI drivers are better these days, but neither ATI or nVidia have great drivers. Well, the drivers are OK, its just a pity that they are closed source. 

I'm a bit suprised that you think that the p4 is holding you back. Its hardly fast these days, but when your running IceWM it thought that it would still be pretty good. If you were running KDE4 with full eyecandy it would be a bit more understandable.  

Power consumption isnt that big an issue, but it does add up over a few years of 24/7 use. Theres power costs, enviormental concerns, and heat build up (which I personally believe is a killer, long term). I dont think that the i7s are a whole new world of speed, and in a few years the difference between an i7 and a C2Q isnt going to be a big as current benchmarking might suggest. Eg. a P4EE blitzed benchmarks back in the day, but your not going to use a few different model P4s and be able to pick the P4EE in desktop use from other similar P4s. 

Its just a pity that the i7s need new motherboards, etc, and you cant run a C2D CPU in them, or else grabbing a C2D now and getting an i7 later when would be a nice option.  (if you feel the need, or when the i7 just junked and Intel moves to yet another new socket/chipset release)

---

### Post by mDuo13 on 2009-10-30
If the P4 wasn't holding me back, I'd actually be fine with sticking to my current machine. (Even though one hard drive died, the other two are intact. They're not RAIDed though.) That desktop is still running Windows; the IceWM is on my Eee. The problem with the P4 is that it can't process all 720p h264 video smoothly, even with CoreAVC. Some videos work fine, some lag. I tried getting a Radeon HD3650 so I could offload the decoding but since I'm also limited to AGP it ended up being slower and less reliable than what I was doing before.

And yes, I agree it's a pity that the i7 and the C2 series have different sockets. Otherwise I would totally get the core2duo now and get the i7 later.

As for environmental/power concerns... I really should care. Maybe now that I don't need apache/mysql to be running all the time (yes I ran my personal website on Windows Apache 1.x for years, on an ADSL connection no less) and especially if I get that SSD, I can actually turn the computer off sometimes... except that I also use my computer's mp3 player as an alarm clock in the morning. Hm.

---

### Post by cascade9 on 2009-10-31
Hmmm, from what I've heard as long as you have an OK processor and a video card with 500Mhz + core, your fine with h.264, but obviously thats not the case. I've played a bit of h.264 on older machines, my old Athlon 2100/6600GT hasnt had any problems with them, but I've had a very limited sample size.

---

