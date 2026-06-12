---
title: "Will this Ubuntu 12.10 box work as an HTPC?"
date: 2013-06-11
forum: Hardware
---

### Post by MediaBanger on 2013-06-11
[http://www.newegg.com/Product/Product.aspx?Item=N82E16883258040](http://www.newegg.com/Product/Product.aspx?Item=N82E16883258040)

I'd be interested in using the above box, which comes with Ubuntu 12.10, for a little streaming as well as doing some work, using my 46-inch RCA LED HDTV as a "monitor."

I've read that Ubuntu 12.10 has some issues with displaying properly to HDMI, which is the way I'd have to hook it up to my TV. The NewEgg product info says the graphics are Intel HD, but doesn't give the model number of the graphics card.

Basically, I want to get rid of a dedicated computer desk because it takes up valuable space in our small home. And I've had good experience converting my 2004 Mac G5 PowerPC over to Linux MintPPC (heavily Ubuntu-based), so this package appeals to me a lot. I just don't want to order it, then find out the box won't work through HDMI without serious updates to the kernel, then pay to send the product back.

Still kind of a newbie at Ubuntu (been reading the forums the last several days, searching on the topic of 12.10 HDMI compatibility) so your patience and assistance is much appreciated. :)

---

### Post by ahallubuntu on 2013-06-11
~

---

### Post by MediaBanger on 2013-06-11
> **ahallubuntu said:**
> The Celeron 1007U, although it is dual core, is a tad slow - only 1.5GHZ. It's also apparently a low-voltage notebook CPU, not a desktop CPU. I would expect limited performance.

You've got to understand this is similar performance to my single-core G5 Mac. Doesn't hurt that the Avatar box has 4 GB compared to my current 512K RAM on the Mac. Also, I currently use an Android 4.0 netbook from this company, and while its web browsing abilities are somewhat hampered by its Allwinner SOC-- general browsing just isn't its cup of tea-- its video streaming capabilities are top-notch.

If I were to buy this box and HDMI had issues displaying properly, how involved would it be to go backward and install 12.04, since I hear that's a lot more likely to be stable with HDMI displays?

---

### Post by ahallubuntu on 2013-06-11
~

---

### Post by MediaBanger on 2013-06-11
> **ahallubuntu said:**
> But you aren't using it as an HTPC (with HDMI) right?

The Mac, no.



> Again, you aren't streaming 720p or 1080p videos with it are you?  Web streaming is not as CPU-intensive as full video.

With the Avatar notebook, yes I am. And it does pretty well. But that's an Allwinner A10 machine, so it's a different beast. And it only has 1 GB RAM, IIRC.

> I'm not saying this box won't be able to do video well - in fact, it should handle it just fine.  But if you try to do anything else at the same time, it will probably slow to a crawl.  This CPU was optimized for low power in a laptop, not as a desktop CPU.

One of the things I'm used to with the Android notebook is single-tasking. Even with the phone-centric Android OS, I can flip between a browser window and Wordpress app, which I do quite a bit. That's pretty much the extent of my work duties. I'm not trying to stream video at the same time I do that kind of stuff.

> I'm guessing that installing 12.04 on this potential hardware should be easy.  It's unusual for a company to sell a computer with an OS that is supported for only 18 months (only ten more months for 12.10), but I'm guessing they did that because 12.04 at the time didn't work on this hardware - but now with the 3.5 kernel 12.04.2 should handle it just fine.  The kernel is the most important thing for hardware support, and 12.10 and 12.04.2 now use the same 3.5 kernel.

This box should be OK.  My personal preference is to look for deals and build my own.

That's the kind of info I'm looking for. I thought it was strange to go with 12.10, as well, but perhaps you're right about the underlying kernel not supporting this hardware when the machine was built. A local Linux user was telling me basically the same thing when I was telling him about this box, so that's encouraging that 12.04 with its long-term support should be usable on this machine-- if not immediately, certainly soon.

---

### Post by papibe on 2013-06-11
Hi MediaBanger.

The main concern for a HTPC (that reproduces HD video) is the video card decoding capabilities.

Since the machine has 'Intel HD Graphics', it would be interesting to review the card's support for the VAAPI library. My first guess is that it is well supported, and players like VLC and XBMC can take advantage of it (please research further because I have more experience with Nvidia than Intel graphics).

In that context, the Celeron CPU shouldn't be an issue at all.

Just my thoughts.
Regards.

---

### Post by Yellow Pasque on 2013-06-11
> I've read that Ubuntu 12.10 has some issues with displaying properly to HDMI
Link/Citation?

---

### Post by MediaBanger on 2013-06-11
> **Temüjin said:**
> Link/Citation?

[http://ubuntuforums.org/showthread.php?t=2073825](http://ubuntuforums.org/showthread.php?t=2073825)

[http://ubuntuforums.org/showthread.php?t=2098333](http://ubuntuforums.org/showthread.php?t=2098333)

This user got his fixed, after some initial issues (especially noteworthy because he/she was using Intel HD Graphics like this Avatar unit has): [http://ubuntuforums.org/showthread.php?t=2094303](http://ubuntuforums.org/showthread.php?t=2094303)

---

### Post by ahallubuntu on 2013-06-11
~

---

### Post by MediaBanger on 2013-06-11
> **ahallubuntu said:**
> NewEgg has a decent Intel motherboard (BOXDZ68DB) on sale today for $59.99
Add Celeron G1610 (dual core 2.6GHZ Ivy Bridge) for $49.99 (a few bucks cheaper at Amazon)
Add 4GB of DDR3 RAM for about $30 (look for 8GB on sale)
Add RAIDMAX Tornado ATX-238WU for $15 after rebate
Add WD5000AAKX 500GB hard drove for $59.99
Add RAIDMAX RX-380K power supply for $15 after rebate

And you have a system for $230 that has better performance, more features, and better expandability than the Avatar for about the same price.  But you'd have more flexibility to configure the custom build (larger hard drive, expand RAM, use an SSD, etc.)  Of course, the Avatar is a "slim PC" so will consume less space - a big plus for some users.

I get you man, and if this wasn't going to be in my living room, I'd probably give building my own system a try just because I like to be hands-on like that. But as it is, my wife already wants to get a smaller TV stand since we upgraded to an LED flat panel from our old RCA CRT monster. So a full-size tower is a nonstarter with her.

---

### Post by ahallubuntu on 2013-06-11
~

---

### Post by MediaBanger on 2013-06-11
> **papibe said:**
> Hi MediaBanger.

The main concern for a HTPC (that reproduces HD video) is the video card decoding capabilities.

Since the machine has 'Intel HD Graphics', it would be interesting to review the card's support for the VAAPI library. My first guess is that it is well supported, and players like VLC and XBMC can take advantage of it (please research further because I have more experience with Nvidia than Intel graphics).

In that context, the Celeron CPU shouldn't be an issue at all.

Just my thoughts.
Regards.

Thanks papibe for this helpful post. Did a search on Intel HD Graphics VAAPI and found [this little gem from Intel]("https://01.org/linuxgraphics/community/vaapi"). Now if I can get someone at Avatar or NewEgg to tell me which card is inside that little box they're selling, I'd feel a lot more confident in deciding whether this machine's for me.

EDIT: And[ this link, also from Intel]("http://ark.intel.com/products/72061/"), would seem to confirm the HD Graphics card on the Celeron 1007U found in this Avatar box can, indeed support HDMI displays. Cautiously optimistic. Now to save some freelance money over the next couple months and give it a try.

---

### Post by Yellow Pasque on 2013-06-12
Intel HD2500 graphics.
[https://en.wikipedia.org/wiki/List_of_Intel_Celeron_microprocessors#.22Ivy_Bridge.22_.2822_nm.29_2](https://en.wikipedia.org/wiki/List_of_Intel_Celeron_microprocessors#.22Ivy_Bridge.22_.2822_nm.29_2)

---

### Post by MediaBanger on 2013-06-12
> **Temüjin said:**
> Intel HD2500 graphics.
[https://en.wikipedia.org/wiki/List_of_Intel_Celeron_microprocessors#.22Ivy_Bridge.22_.2822_nm.29_2](https://en.wikipedia.org/wiki/List_of_Intel_Celeron_microprocessors#.22Ivy_Bridge.22_.2822_nm.29_2)

Good find, thanks! This backs up the info found in the Intel processor info page I posted above, which is good to see.

Research continues. For now, won't be able to buy the box for a few weeks at the earliest because my truck battery had a sudden (like, within five minutes of a perfect start-up) failure. Strangest battery failure I've ever experienced. The replacement battery cost me more than half what the computer will cost. :( Gotta save a little longer now!

---

