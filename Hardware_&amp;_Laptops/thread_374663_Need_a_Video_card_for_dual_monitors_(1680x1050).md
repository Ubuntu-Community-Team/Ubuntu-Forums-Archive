---
title: "Need a Video card for dual monitors (1680x1050)"
date: 2007-03-02
forum: Hardware &amp; Laptops
---

### Post by caffienda on 2007-03-02
I am in the process of building a new computer and I want to make sure the hardware is Linux friendly.   I want to run dual monitors that have a resolution of 1680x1050, so what video card would support this? Or would I need 2 cards?

My MOBO/CPU is going to be a Intel BadAxe2/E6600 w/ 2x 2GB ECC PC6400 DDR2.

Anyone have suggestions as to a dual monitor card for this system?

---

### Post by deathshadow on 2007-03-02
Your BEST bet is going to be a dual head nVidia card. With the binary drivers that gets you twinview, and it works halfway decent with Xinerama without the binary drivers (if you are one of those 'free as in freedom only' nutjobs)

If on a budget, I'd suggest a 7900GS... it's only a few bucks more than the 7600GS, same price as the 7600GT yet clocks in 50% faster than the 7600GS and twice as fast as the 7600GT on most benchmarks

NewEgg good as always:
[http://www.newegg.com/Product/Product.asp?Item=N82E16814133186](http://www.newegg.com/Product/Product.asp?Item=N82E16814133186)

and if money is no object, there's always the 8800GTS series... There's no REAL reason to buy more than this right now.
[http://www.newegg.com/Product/Product.asp?Item=N82E16814130082](http://www.newegg.com/Product/Product.asp?Item=N82E16814130082)

A word of warning about multiple display though - convincing openGL applications to run fullscreen NOT half and half on each display is tricky (if not impossible in some apps), even GETTING openGL working right can be several HOURS of headaches, going for more than two displays is buggy and painful... pretty much the X11 implementations when it comes to multiple displays STILL haven't caught up to Windows 3.1 with a targa board, or an early 90's apple.

---

### Post by caffienda on 2007-03-02
Wow, I can't believe how much video applications are limited in Linux.  Seems pretty sad (not trying to knock it).  I wish there was a more robust solution.  

Why is there such limited ability in Linux?  Is it that source code for the drivers isn't available?

---

### Post by deathshadow on 2007-03-02
> **caffienda said:**
> Wow, I can't believe how much video applications are limited in Linux.  Seems pretty sad (not trying to knock it).  I wish there was a more robust solution.  

Why is there such limited ability in Linux?  Is it that source code for the drivers isn't available?

It's just not been considered a priority, so efforts in that regard have lagged or even been non-existant until recently (past... three years or so). Just getting video drivers working on a single display has been ice-skating uphill for the *nix world in general (just look at all the posts from people who still end up falling back on the VESA drivers)

Like a lot of open source projects, you have this issue that since nobody's paying for it, you are relying on the free time of people with day jobs - and if nobody with the knowledge to implement it actually has an interest in doing it, you'll never see it implemented properly, if at all... Which is why you'll see statements like "if it matters that much to you, code it yourself" followed by the person from the Windows or MacOS world who's been doing "fill in the blank subject" flawless for a decade and a half without a lick of programming knowledge respond "**** this, I'm going back" (usually graphic artists and gamers)

It's why I recommend the nVidia cards with the binary (non-OSS) drivers - it actually has money and paid employees behind it and therin incentive for things like dual display to work PROPERLY... Which is probably part of why they 'faked' xinerama's 'display reporting' api and implemented their own system (twinview) in the first place. (Just as ATI has done with it's own 'MergedFB')

Of course, part of the problem stems from that dated pile of hacks known as X11, which really was never meant to run multiple displays as a single unit in the first place (which is odd given the 'multiple desktop' and 'remote access' thing that is it's cornersone) - much less run something like OpenGL fullscreen. It's much akin to trying to run DX2, Glide or WinG on Windows 3.1 - (in a LOT of ways, it feels like the old Voodoo GLIDE implementation) which is why from time to time I've been known to say that in a LOT of regards Linux on the whole hasn't caught up to Win 3.1 as a desktop OS from a usability or reliability standpoint.

Linux itself may be reliable as all get, but X - well, I've killed and restarted X at least five times more often than I ever have to reboot windows... and when all the applications you are using rely on X, the net effect is much the same.

As always, EVERYTHING has shortcomings... you just have to be wary of people who are willing to ignore them with the 'head in the sand' routine.

---

### Post by caffienda on 2007-03-02
Thanks for the explanation, it's much clearer now.  I wasn't implying that I was pissed that there wasn't support, just disappointed.

---

