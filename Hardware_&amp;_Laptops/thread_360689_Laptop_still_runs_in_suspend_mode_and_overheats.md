---
title: "Laptop still runs in suspend mode and overheats?"
date: 2007-02-13
forum: Hardware &amp; Laptops
---

### Post by SnowPunk98 on 2007-02-13
So I setup my Ubuntu (Edgy) to go into suspend on my E1705 laptop when I close it. So I closed it last night and threw it in my bag, I came back in later and heard the fan running at what sounded like full speed.

When I pulled it out it was really hot and seemed like it was not truly in a suspended state. Is this a known issue, or did I set it up wrong, or whats going on?

---

### Post by magicrobotmonkey on 2007-02-16
I have the same problem with mine - it turns back on after a while, and even if it doesn't its stays really hot, so I dont think it really works. I can add that my power light starts blinking like it used to when suspend used to work (waay back in the beginning of dapper, one of the first kernel updates broke it and it hasn't work since), so some of the hardware thinks its suspended, but I can tell its really not, because when it used to work the keyboard leds and the wifi and bt leds would go off. When its not working, all the keyboard leds and the bt led come on. 

I'm not sure how to debug it, I've tried to look at system messages, but I don't see anything in there that jumps out at me as a problem.

---

### Post by djembe330 on 2007-02-21
I am having the exact same problem.  Hibernation is working, but suspend goes into some "almost suspended" state.  The CPU is still powered on (fans will kick on periodically) and the keyboard lights (the "locks", wireless, bluetooth indicators) stay on.  The power light flashes though, so some parts of the system seem to think it is suspended.  

I think it might have something to do with SMP and possibly frequency scaling...but that is just a guess.  I got it to suspend fully once before (I think it was after coming back from hibernation), but not again since then.

On a related note I fixed a frequency-scaling issue with hibernation by following this link:

[http://www.ubuntuforums.org/showpost.php?p=1791164&postcount=21](http://www.ubuntuforums.org/showpost.php?p=1791164&postcount=21)

Maybe it is some related issue?

---

### Post by SnowPunk98 on 2007-02-22
Is it just me or do laptops seem very difficult to get working correctly using Linux?

---

### Post by djembe330 on 2007-02-22
Laptops are not that much harder than desktops to get working in Linux.  It is mainly the fact that hardware developers are not opening the specifications of their hardware to open source developers.  This can make it very difficult, or impossible, to write fully functional drivers.

A friend of mine has suspend/hibernate working flawlessly "out of the box" on his laptop, but still can't get it to work on his desktop.  

Linux can be a headache to install...but I find that it is definitely worth it - for the learning experience as well as the end-product.  Even my fiance dreads booting back into M$ now!

Now, does anyone know about this suspend issue?  ;)

It has to be a simple solution...something is just getting hung up on shutting down the processor(s)...but what?

Are there any error logs that may be useful?  Maybe everyone that is experiencing this problem could compare?

---

### Post by djembe330 on 2007-03-04
I may have found the solution...

And surprise surprise, it doesn't look like it is the fault of linux...but of the BIOS!

I booted into M$ for the first time in a long while (just to remember why I hate it) and an update popped up (along with about 15 other things) that said there is a new BIOS available.  I had A05 and it installed A12.

After I booted back into Ubuntu, I thought "what the heck maybe a bios update will fix suspend."

And it did!  At least so far...

I believe there is probably a way to update the bios from linux too, but I'm not sure.  Post back and maybe we can compare which versions of the BIOS we have, and narrow it down to that.

PS - Updated the BIOS is potentially hazardous to your computers health, so do so at your own risk.

---

