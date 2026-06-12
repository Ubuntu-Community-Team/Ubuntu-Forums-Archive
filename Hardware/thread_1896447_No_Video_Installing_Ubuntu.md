---
title: "No Video Installing Ubuntu"
date: 2011-12-17
forum: Hardware
---

### Post by weyemar on 2011-12-17
I recently purchased an HP laptop.

When I boot to the Ubuntu disc, I hear the disc drive active but the screen goes completely black.

Laptop is a dv6-6135DX

Spec: [http://www.newegg.com/Product/Product.aspx?Item=N82E16834158073]("http://www.newegg.com/Product/Product.aspx?Item=N82E16834158073")

Thanks for any help.

(I have a feeling it might switch to the VGA out or HDMI out..maybe?)

---

### Post by N00b-un-2 on 2011-12-17
Your first mistake was wasting money on an HP product, and one with a an ATI graphics card at that.  And an oddly configured and poorly supported one at that! (and refurbished at that!  VERY VERY VERY VERY bad combo IMHO).
So here is the crux of the situation:
The graphics card supports "Crossfire" switchable graphics and is in fact two entirely separate GPUs; an ATI 6750M and a lower powered ATI 6620.  So it sounds like it is either defaulting to a display that is not your laptop screen (certainly possible on a goofy setup like this), or simply failing to initialize graphics entirely (most likely).
First try plugging a monitor into and booting up to see what happens.  If you still get no video out put then you need to check your BIOS settings and see if its possible to disable the multiple GPU function, and only after installing the proprietary drivers for your system you may be able to turn crossfire back on in BIOS, but be aware that AMD's website indicates that "hot switching" is not supported on Linux without restarting the X server essentially negating the benefit of the dual graphics cards, so you are stuck running the hotter 6750M full time or the lower powered (and thus lower power drain) 6620.  So basically, to be able to actually utilize the technology in your laptop you have to run Windows as it's not supported on Linux.  I ran into a problem with having to disable multiple GPUs on an Alienware Laptop before install, YMMV.
Good luck.  Is it too late to return the laptop and get something that actually works on Linux?

---

### Post by weyemar on 2011-12-17
Running Windows 7 Ultimate, I have had an amazing experience with this laptop. I runs great and packs a lot of performance. However, it is very unfortunate to hear that this laptop is poorly supported for Linux. I am a novice when it comes to Linux but was hoping to learn.

I will try the bios option and if that doesn't work, I'll plug in a VGA monitor.

Thanks for the help!

---

### Post by N00b-un-2 on 2011-12-21
Any luck yet?

---

### Post by redlsteg on 2011-12-21
My wife's HP laptop had the same issue when I tested Ubuntu on it. Turns out the display brightness defaults to 0 on boot. I believe there is a script you can run to change it.  In the meantime you can just press the function keys to increase brightness.

---

### Post by N00b-un-2 on 2011-12-22
back lighting set to 0 should still result in a visible screen.  No backlighting whatsoever means the screen is turned off.  As for a script, it would be hardware specific.

---

### Post by Mark Phelps on 2011-12-22
> **weyemar said:**
> Running Windows 7 Ultimate, I have had an amazing experience with this laptop. I runs great and packs a lot of performance. However, it is very unfortunate to hear that this laptop is poorly supported for Linux. I am a novice when it comes to Linux but was hoping to learn.

Unlike others, I am not going to slam you for buying a product, that apparently, is providing you an "amazing experience"!

Unfortunately, this hybrid graphics problem is not the first time (and probably, won't be the last) in which PC vendors have introduced new hardware-based features that are only supported in Windows.  After all, they sell PCs, and the vast majority of PC sold contain Windows (like it or not).  So THAT is the market they see helping them sell their products.

The only mistake you made -- and it's a common one for folks new to the Linux community -- is not using an internet search engine to check on the availability of hybrid graphics (or switchable graphics) support in Linux before you bought the PC.  Had you done that, you would have found out that it's not well supported, it's not going to be a trivial problem to solve, and it's not even going to be included in Ubuntu 12.x.

So, don't beat yourself up for this.  You did what most folks do -- presumed that Linux would automatically support the latest and greatest hardware out there.

---

### Post by N00b-un-2 on 2011-12-28
I was not bashing the OP, I simply boycott HP and openly discourage people from supporting this company by spending their hard earned money on HP products.  In my lifetime I would like to see the HP business empire collapse and disappear. The fact that the OP's laptop utilizes hybrid graphics just fine on Windows has nothing to do with my statement, as you said hybrid graphics does not work well on Linux yet.  I'm not a Windows basher either, I use Windows nearly as frequently as I use Linux.  And I would NEVER assume that ANY hardware works on Linux without researching it extensively.  I recently made the mistake of purchasing a TV Tuner card that the Hauppage web site explicitly states is supported on Linux, but I came to find out that only the Digital tuner part is supported on Linux meaning that I can't watch cable TV at all on Linux.  Manufacturers seldom provide Linux drivers for their products when they release them, if at all and when they do release drivers they are often closed source.  A large amount of hardware support for the Linux kernel is in fact the result of reverse engineering of such closed source or proprietary code, for example the ATI and nVidia drivers for linux.  There are open source Linux drivers available for both which are both the result of reverse engineering of the closed source drivers, but in order to effectively use your card to its full potential you have to install the proprietary drivers.

---

