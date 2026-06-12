---
title: "Is the Intel Atom N450 1.66 GHz CPU sufficient for me?"
date: 2011-06-25
forum: Hardware
---

### Post by DavidVS on 2011-06-25
I think I am about to buy a [Terra HD]("http://zareason.com/shop/Terra-HD.html") from ZaReason.  For my price limit of $700 I can get the model with 2 GB RAM, 80 GB solid state drive, and 8 hours of battery life.

My only concern is that my mother-in-law has an HP Mini 110, which has the slightly newer Intel Atom N455 processor -- and her netbook is slow as molasses.

I realize that her Windows 7 Starter is a resource hog.  She does not have a solid state drive.  (Perhaps she has accidentally acquired some spyware or something too, although I doubt it since her husband is quite computer savvy and also uses that netbook.)  But I am still worried.

**But could folks with an Atom N450 1.66 GHz CPU confirm that it is acceptably fast for using your linux interface, file copying, text editing, FTP, text web page browsing, AVI playback, and Skype?**

Please include if you are using Ubuntu 11.04, an older Ubuntu, or another flavor of linux.  Thanks!

---

### Post by prshah on 2011-06-25
> **DavidVS said:**
> 
**But could folks with an Atom N450 1.66 GHz CPU confirm that it is acceptably fast for using your linux interface, file copying, text editing, FTP, text web page browsing, AVI playback, and Skype?**

Hello, I am using a Lenovo S10-3t (2GB RAM) with
```
Sat Jun 25 @12:43:16:~$ cat /proc/cpuinfo |grep -i name
model name	: Intel(R) Atom(TM) CPU N450   @ 1.66GHz
model name	: Intel(R) Atom(TM) CPU N450   @ 1.66GHz
```

and I find the performance quite good, much better than just "acceptable". The pre-installed Windows 7 home basic is quite sluggish, but Ubuntu is responsive and smooth.

I'm using Ubuntu 10.10 64-bit, and everything works fine, including video playback, Flash, Skype and light gaming.

I recently built a desktop with this chip (though only 1GB RAM), and installed Ubuntu 11.04 on that. Unity2D (Unity/3D didn't run) is a huge drag, and the interface feels sluggish, but programs perform well. 

I assume it will be good enough for your day-to-day needs, but try to have atleast 2GB RAM. A good graphics card (instead of onboard) should make it fairly zippy, if you feel the performance is not enough. 

Bottom line: I'm happy with it's performance, but I assume that you need atleast 2GB of RAM for "modern" operating systems. Mine is with a "conventional" SATA HDD, so with an SSD, it should fairly fly for day-to-day work.

---

### Post by Gyokuro on 2011-06-25
I'm an owner of a HP Mini 210 ( [http://www.shopping.hp.com/webapp/series/category/notebooks/mini210_series/3/computer_store](http://www.shopping.hp.com/webapp/series/category/notebooks/mini210_series/3/computer_store)) and I can do below mentioned task (however I have optimized the system) but sometimes it's too slow for videos but that depends on the used codec and resolution.  But I'm happy with it :popcorn:

Next netbook should have an NVIDIA ION - tested an Acer AspireRevo and even FullHD's videos are not a problem with this product.

---

### Post by Arsic on 2011-06-25
The N455 is a single core with hyperthreading. The only other difference between that and a N450 is that the N455 has DDR3 RAM support. You can get 1080p local playback with CoreAVC and Wine, but 720 and 1080 resolutions can't be streamed unless you have an N550 with integrated NVIDIA ION 2 in addition to the stock Intel GMA 3150 GPU.

---

### Post by Gyokuro on 2011-06-25
I'm aware about the specs and that's the reason why my next netbook should have NVidia ION - MPlayer with VDPAU should handle 1080p videos fine (with NVidia blob).

---

### Post by DavidVS on 2011-06-26
To those who mention the NVidia ION or NVidia ION 2 -- can you recommend an affordable 11" to 13" netbook with that video card and a solid state drive?

I do not care much about watching a movie in a window or full screen, but am curious for the sake of gaming.

Thanks!

---

### Post by Yellow Pasque on 2011-06-26
I'd rather go AMD at this price point, like HP dm1z. I spec'd one out and it comes out to same price as the TerraHD, but it has an E-350 dual-core, better graphics for gaming (RadeonHD 6310m), 3GB RAM, 128GB SSD.

ION might be good too, but make sure you do not get a model with switchable graphics (Nvidia calls it Optimus).

EDIT: Single core Atom might be okay with a regular hard disk that bottlenecks a lot of your computing, but with an SSD and paying that much money, I would want a CPU that wouldn't noticeably slow things down.

---

### Post by DavidVS on 2011-06-26
> I'd rather go AMD at this price point, like HP dm1z. I spec'd one out and it comes out to same price as the TerraHD, but it has an E-350 dual-core, better graphics for gaming (RadeonHD 6310m), 3GB RAM, 128GB SSD.

ION might be good too, but make sure you do not get a model with switchable graphics (Nvidia calls it Optimus).

EDIT: Single core Atom might be okay with a regular hard disk that bottlenecks a lot of your computing, but with an SSD and paying that much money, I would want a CPU that wouldn't noticeably slow things down.

I do understand, but might ignore this good advice for personal reasons.

I have done no 3D gaming in 3 years.  I have fought with making Ubuntu work on my laptop.  So for the same price, I am disposed to use a linux-friendly vendor even if it cripples my potential for 3D gaming.

Even the ability to use *any one* 3D game would feel like a new treat.  Using the newer or better games is irrelevant to me.

I did ask about an Optimus system, but was [warned against]("http://ubuntuforums.org/showthread.php?t=1790428") those.

**EDIT:** I should add that i use *AVIDemux* to chop off the ends of Flip videos before posting them [online]("http://blip.tv/posts/view/?user=davidvs&pagelen=96&sort=date").  As long as the computer can handle that at reasonable speeds, I am happy.

---

