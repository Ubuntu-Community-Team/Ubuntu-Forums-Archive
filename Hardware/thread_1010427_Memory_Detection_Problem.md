---
title: "Memory Detection Problem"
date: 2008-12-13
forum: Hardware
---

### Post by Vargas on 2008-12-13
Hi guys, I was wondering if you can help me with this.

Until today I had 2GB of ram PC6400 800MHz and everything worked just fine.
I decided to upgrade to 2x2GB (4GB total) of the same characteristics: PC6400 800MHz.

I have both XP SP3 and Ubunutu 8.10 on 32bit. I am perfectly aware of the memory size detection limit due to the 32bit but I also know that I should at least be detecting 3GB of RAM. The problem?? No matter what I do, I can only see 2.5GB on both XP and Ubuntu.

Everything is updated; Windows, Ubuntu, BIOS, everything...
I have a K9N SLI Platinum motherboard with AMD X2 5600+
I have the dims on slots 1 and 3 (I also tried 1 and 2 and it's the same).
Not exactly sure what else can I try since the BIOS detects all 4GB.

Any suggestions will be very appreciated. :D

---

### Post by jpkotta on 2008-12-13
I saw this just last week.  We had a ridiculous gaming machine at work (long story) and it had 4 GB installed.  The BIOS saw all 4 GB, but Windows XP saw 2.5 GB.  It had 2 SLI video cards with 768 MB each.  4096-2*768 = 2560.  The video cards stole the address space from the main memory, and the only way around that is a 64-bit OS or less video memory.

---

### Post by Vargas on 2008-12-16
> **jpkotta said:**
> I saw this just last week.  We had a ridiculous gaming machine at work (long story) and it had 4 GB installed.  The BIOS saw all 4 GB, but Windows XP saw 2.5 GB.  It had 2 SLI video cards with 768 MB each.  4096-2*768 = 2560.  The video cards stole the address space from the main memory, and the only way around that is a 64-bit OS or less video memory.

Well like I said before, I do know the limitations of a 32-bit OS
but when then is it only detecting 2.5GB and not 3GB as it should?
I just don't get it.

---

### Post by jpkotta on 2008-12-17
So you don't have a ton of video memory (that is, on the video card)?  And you don't have any other peripheral that have their own (large amounts of) memory?  Then I'm not really sure.

Since you have 64-bit HW, try running a 64-bit live CD.

---

### Post by Vargas on 2008-12-17
> **jpkotta said:**
> So you don't have a ton of video memory (that is, on the video card)?  And you don't have any other peripheral that have their own (large amounts of) memory?  Then I'm not really sure.

Since you have 64-bit HW, try running a 64-bit live CD.

I have a GeForce 8500GT w/ 512MB
I would normally think this is related but a friend of mine who bought this same memory also has a 512MB video card but his XP 32bit IS detecting 3GB.

---

### Post by icanfly0307 on 2008-12-17
If your video card uses 512 MB, then you'll only be able to see 2.5 GB in XP or Ubuntu. (3 GB - .5 GB = 2.5 GB) :grin:

If your friend's computer can see 3 GB with the same amount of video RAM, it might be that he has a *dedicated* graphics  card. That way, it won't use system RAM and you'll keep seeing 3 GB. 

If you want to get a full 4GB in Ubuntu (which you want, right? :)), I would recommend compiling a custom kernel. Of course, it you don't want to try that, you can always Google around for help or post back here.


Hope that Helps. :)

---

### Post by Vargas on 2008-12-17
> **icanfly0307 said:**
> If your video card uses 512 MB, then you'll only be able to see 2.5 GB in XP or Ubuntu. (3 GB - .5 GB = 2.5 GB) :grin:

If your friend's computer can see 3 GB with the same amount of video RAM, it might be that he has a *dedicated* graphics  card. That way, it won't use system RAM and you'll keep seeing 3 GB. 

If you want to get a full 4GB in Ubuntu (which you want, right? :)), I would recommend compiling a custom kernel. Of course, it you don't want to try that, you can always Google around for help or post back here.


Hope that Helps. :)

My friend currently has a GeForce 8400 with also 512MB.
I have a 8500 with 512MB
Nothing shared, nothing of the sort. All dedicated.
His sees 3GB mine 2.5GB
That's what I don't get.
Still, I might just try Vista 64 and Ubuntu 8.10 64 since Vista 64 sucks less than XP64

---

### Post by icanfly0307 on 2008-12-17
Are you sure your graphics card is dedicated? Look around in the BIOS for any RAM related options that might be sucking it up.

---

### Post by johnnychcr on 2008-12-17
I now have Vista 64X and it detects the 4 gigs no problem....some programs actually runs faster than Xp......

---

### Post by jpkotta on 2008-12-18
> **icanfly0307 said:**
> Are you sure your graphics card is dedicated? Look around in the BIOS for any RAM related options that might be sucking it up.

In my case, it was precisely *because* the video memory was dedicated that the RAM disappeared.  It was not using up the RAM, it was using up the *address space* (which is limited to 4GB on 32-bit HW, as we all know).  If it was sharing memory with the system, I would have seen the memory, just not been able to use it (I think, it's been a long time since I had integrated video).

Well, sounds like OP got it working anyway.  64-bit is easier than people think.

---

### Post by vpsville on 2008-12-18
Ubuntu is *not* limited to 4GB on 32bit systems.  If you enable PAE, it will recognize and utilize up to 64GB of memory on a 32bit system:

[http://en.wikipedia.org/wiki/Physical_Address_Extension](http://en.wikipedia.org/wiki/Physical_Address_Extension)

To enable it you either roll your own kernel, or install the server version of Ubuntu.

---

### Post by soldier1st on 2010-07-13
> **vpsville said:**
> Ubuntu is *not* limited to 4GB on 32bit systems.  If you enable PAE, it will recognize and utilize up to 64GB of memory on a 32bit system:

[http://en.wikipedia.org/wiki/Physical_Address_Extension](http://en.wikipedia.org/wiki/Physical_Address_Extension)

To enable it you either roll your own kernel, or install the server version of Ubuntu.
so what your saying is that even though the bios allows you to use 2.5gb out of the 3gb that enabling pae will allow it to use that extra 512mb? under windows it did not but not sure under linux.

---

