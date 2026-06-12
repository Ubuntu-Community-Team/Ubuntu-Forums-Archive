---
title: "EPIA MEII 6000 Compatible ?"
date: 2005-04-26
forum: Hardware &amp; Laptops
---

### Post by ks- on 2005-04-26
Quick question... I'm about to buy a VIA EPIA MEII 6000 motherboard. I was wondering, will my system be compatible with Hoary ? Can I encounter some problems ?

I'm new to linux in general but after trying it, I fell in love with ubuntu and I'm building myself a new system just for it :)

Thanks for your replies.

---

### Post by ks- on 2005-04-28
*bump*

---

### Post by ubnik on 2005-05-04
[QUOTE=ks-]Quick question... I'm about to buy a VIA EPIA MEII 6000 motherboard. I was wondering, will my system be compatible with Hoary ? Can I encounter some problems ?

I'm new to linux in general but after trying it, I fell in love with ubuntu and I'm building myself a new system just for it :)

Thanks for your replies.[/QUOTE]
 If its anything like the MEII 1200 that I tried installing with warty a few months ago, you will probably find that it is not straight-forward.  You will almost certainly have to  go to some lengths to get video, sound and encryption hardware working nicely.  epios.net is a linux project that has just started which might mean that this hardware is better supported in other linux distros.

NB the hoary default install more or less works, with no sound and the video is quite horrid - and you will find the system is quite slow.

If you are keen to experiment with low-power consuming hardware, I'd suggest looking into a mac mini.  It looks like support for this stuff is already good.  Somewhere in here there is a guy that has posted a kernel image that gets all the basics working and you can just apt-get it.  sorry don't have time to find the URL now.

---

### Post by superhac007 on 2005-05-04
I have installed warty and hoary on both the EPIA PD 600 and EPIA PD 1000.  Works great!

---

### Post by paxmark on 2005-05-04
[QUOTE=ks-]Quick question... I'm about to buy a VIA EPIA MEII 6000 motherboard. I was wondering, will my system be compatible with Hoary ? Can I encounter some problems ?

I'm new to linux in general but after trying it, I fell in love with ubuntu and I'm building myself a new system just for it :)

Thanks for your replies.[/QUOTE]
 VIA has made a lot of progress in the last two years.  I bought a EPIA two years ago.  Mandrake 8 needed to compile the kernel to get my EPIA U-BUDDY to work, my first kernel compilation.  But Mandrake 9 went on a lot easier, the vanilla kernel worked.  It worked fairly well until it started making noise.  I went 12 weeks in RMA hell, and finally ECS sent me a UBuddy with more memory, twice the hard drive, but I had to put a P-4 in the new motherboard.  The voltage regulator on that entire series was bad.  

Also, it was a lot easier to get the drivers on by installing windows (dual boot).  I just had a heckuva time getting drivers in via Linux.  

Check around around about the security system they are starting up on the web.  It might be easy, it might be hard. 

If you are going to go with the EPIA - the question might not be how do I install Ubuntu onto the system, but what distribution works best with this system.  You say you are not that experienced.  A new operating system and a new motherboard are two learning curves, granted they do tie together at points.  

How much work do you want this to be, how much time do you have, what are you going to do with this system.  I am not trying to dissuade you - if the price were better -I would go the same way again with an EPIA, 1200 mhz (a slow 1200 mhz at that) and 256 mb ram is enough for my computing needs.

I just got my tax refund back.  I am seriously considering a Mac mini.

---

### Post by ks- on 2005-05-07
Thanks for your replies.

It seems I'll have some hard times installing hoary on an EPIA. Actually, I'm just looking to built myself a small and silent system. I already own a Shuttle (SN45G2), with a WinXP running on it. I want a separate box for my Ubuntu, but I'd like it to be SILENT. and SMALL.

So far, the EPIA seemed the best solution to my problems. But apparently not.

I don't know what to do anymore... :(

---

### Post by ubnik on 2005-05-07
Here is the mac mini man's page.  He's done all the hard work for you:

[http://www.pvv.org/~perchrh/macmini/](http://www.pvv.org/~perchrh/macmini/)

And here is a forum thread with a bit of relevant discussion

[http://ubuntuforums.org/archive/index.php/t-22257.html](http://ubuntuforums.org/archive/index.php/t-22257.html)

This would be my choice for a near-silent, low-watts machine.  I'd expect it to be more responsive than any of the current EPIA-based machines too.

Have a look at this for a performance comparison:

[http://www.extremetech.com/article2/0,1558,1774465,00.asp](http://www.extremetech.com/article2/0,1558,1774465,00.asp)

---

