---
title: "Request for advice: server (PAE) kernel or 64 bit?"
date: 2009-01-17
forum: Installation &amp; Upgrades
---

### Post by chmac on 2009-01-17
Hola,

I just got a new laptop, a Lenovo X301. I currently have 2Gb RAM and plan to add a second 2Gb dimm taking the total to 4Gb. I use the machine as my primary workstation / desktop. I spend quite a lot of time working from battery, so power optimisation is important to me.

I'm considering either the server kernel for PAE support or switching to 64bit Ubuntu. I believe both options will allow me to use all 4Gb of RAM.

I've read about some software issues on 64bit systems. Particularly proprietary software like flash / skype. I need both of these and I also use Zend Studio (java based).

My question is, would you recommend the server kernel or a 64 bit install?

---

### Post by chmac on 2009-01-23
Anyone? bump...

---

### Post by jrusso2 on 2009-01-23
I would use 64 bit if you want to use all your memory. PAE is a hack and won't be used by programs.  It will just show the memory for the operating system mostly.

---

### Post by chmac on 2009-01-23
jrusso2, thanks for the info. I understand that more than ~3.2Gb of memory won't be available to a single thread, but I believe that cumulatively, all my processes will be able to make use of a total of more than 3.2Gb. Is that correct?

I'm a little hesitant over switching to 64 bit because I make regular use of Skype, flash and Zend Studio. I believe there have been problems with these in the past on 64 bit systems.

---

### Post by jrusso2 on 2009-01-23
> **chmac said:**
> jrusso2, thanks for the info. I understand that more than ~3.2Gb of memory won't be available to a single thread, but I believe that cumulatively, all my processes will be able to make use of a total of more than 3.2Gb. Is that correct?

I'm a little hesitant over switching to 64 bit because I make regular use of Skype, flash and Zend Studio. I believe there have been problems with these in the past on 64 bit systems.

I don't use 64 bit but the people on the 64 bit forum seem to feel all those issues have been solved not sure about the skype and zend studio though.

But having the extra memory show and being able to use it are two different things.  In order for an app to use PAE memory it has to be developed to do it and I understand most are not.

But if your happy with 3.2 gigs of memory then stick with 32 bit.

---

### Post by chmac on 2009-01-23
jrusso2, wow, thanks for the follow up. I didn't realise apps had to be specifically developed to utilise PAE memory. That does significantly change things. I'll need to do some more research on that front. I thought PAE was essentially a kernel hack which "fooled" apps into thinking they were using the same memory as other apps by rewriting the addresses (in my very limited understanding of such things!).

More research into this is required on my part I think...

---

### Post by chmac on 2009-02-11
> **jrusso2 said:**
> But having the extra memory show and being able to use it are two different things.  In order for an app to use PAE memory it has to be developed to do it and I understand most are not.

I've was reading the [wikipedia article on PAE]("http://en.wikipedia.org/wiki/Physical_Address_Extension") and as I understand it, PAE is invisible to an individual application. Yes, a single thread can only access up to 3.2Gb or 4Gb of memory, but collectively, applications can use all the available memory.

jrusso2, does that sound right to you?

---

### Post by harry70 on 2009-04-09
> **chmac said:**
> I've was reading the [wikipedia article on PAE]("http://en.wikipedia.org/wiki/Physical_Address_Extension") and as I understand it, PAE is invisible to an individual application. Yes, a single thread can only access up to 3.2Gb or 4Gb of memory, but collectively, applications can use all the available memory.

jrusso2, does that sound right to you?

My understand is same as you and wiki article. So which way did you go? Why?

I'm leaning towards taking the 64-bit plunge now rather than wait a year or two and having to deal with the change then. I assume in 1-3 years, the default will move to 64-bit, but who knows, there may be co-existance with PAE for years to come.

---

### Post by 73ckn797 on 2009-04-09
I run 64 bit 8.10 and 9.04. My system has 4Gib memory. The 64 bit shows 3.8Gib memory. The 32 bit shows 3.2Gib Memory.

Java & flash work just fine. Actually 9.04 64 bit only needs to install the repositories available sun-java and flash-plugin to get working. I do not use Skype so I cannot offer anything about that.

---

### Post by chmac on 2009-04-09
Personally I'm still waiting to buy the extra 2Gb of memory so I'm still running 32 bit standard. I'm thinking I'll switch to 64 bit 9.04 when it comes out. I'm pretty sure skype / flash / java all run ok on 64 bit, I've heard various reports from pepole and it all seemed to work fine.

---

### Post by harry70 on 2009-04-09
> **73ckn797 said:**
> I run 64 bit 8.10 and 9.04. My system has 4Gib memory. The 64 bit shows 3.8Gib memory. The 32 bit shows 3.2Gib Memory.

Java & flash work just fine. Actually 9.04 64 bit only needs to install the repositories available sun-java and flash-plugin to get working. I do not use Skype so I cannot offer anything about that.

Thanks! I was considering staying with 8.10 or even going backwards with 8.04 LTS, but now I'm itching to jump ahead. Might as well take the plunge with 9.04 64 bits all at once. I'll wait for the official release at the end of the month though, so I don't have to make another update on short order. 

Going thru the FAQ, there were several threads in 2006 and 2007 debating the issue, but it's 2009 now and looks like annedotally the issue with Java and Flash are resolved. Probably Wine too. I recall scanning a thread about Skype, so if there is still an issue, there should also be a fix. Seems like most common objections are now behind us. 

If I see the same 3.8GB, that will bug me if it's not the onboard video. What's chewing up your .2GB? Video? Seems like you're running a memory card, so shouldn't be the reason for missing memory. It's only 5%, but right now, I'm testing 8.10 32 bit on new system (burnin) and maximum ram usage has been just a bit over 512MB. Not a byte of swap used yet. Still, seems a waste not to tune it properly and possibly take full advantage of maximum potential. Might even get a graphics card to free up that last ounce of memory.

% free -m
             total       used       free     shared    buffers     cached
Mem:          3162       2811        351          0        264       2073
-/+ buffers/cache:        473       2689
Swap:         4690          0       4690

% uptime
 15:09:55 up 5 days,  1:50,  2 users,  load average: 0.08, 0.10, 0.09

---

### Post by 73ckn797 on 2009-04-09
> **harry70 said:**
> Thanks! I was considering staying with 8.10 or even going backwards with 8.04 LTS, but now I'm itching to jump ahead. Might as well take the plunge with 9.04 64 bits all at once. I'll wait for the official release at the end of the month though, so I don't have to make another update on short order. 

Going thru the FAQ, there were several threads in 2006 and 2007 debating the issue, but it's 2009 now and looks like annedotally the issue with Java and Flash are resolved. Probably Wine too. I recall scanning a thread about Skype, so if there is still an issue, there should also be a fix. Seems like most common objections are now behind us. 

If I see the same 3.8GB, that will bug me if it's not the onboard video. What's chewing up your .2GB? Video? Seems like you're running a memory card, so shouldn't be the reason for missing memory. It's only 5%, but right now, I'm testing 8.10 32 bit on new system (burnin) and maximum ram usage has been just a bit over 512MB. Not a byte of swap used yet. Still, seems a waste not to tune it properly and possibly take full advantage of maximum potential. Might even get a graphics card to free up that last ounce of memory.

% free -m
             total       used       free     shared    buffers     cached
Mem:          3162       2811        351          0        264       2073
-/+ buffers/cache:        473       2689
Swap:         4690          0       4690

% uptime
 15:09:55 up 5 days,  1:50,  2 users,  load average: 0.08, 0.10, 0.09

I believe that it is the way ram is read by the system. There are several past threads discussing how bytes are figured with different systems.

---

### Post by harry70 on 2009-04-13
> **73ckn797 said:**
> I believe that it is the way ram is read by the system. There are several past threads discussing how bytes are figured with different systems.

Just a couple of thoughts, but have you remapped memory in bios and disabled the onboard video? I'll be doing that to the extent the BIOS can handle that and I hope to see the full 4GB when I get there.

[http://ubuntuforums.org/showthread.php?t=979441](http://ubuntuforums.org/showthread.php?t=979441)

---

### Post by chmac on 2009-04-13
harry70, as I understand it (and I may be wrong), you cannot have 4Gb of usable memory on a 32 bit system. Some memory addresses are reserved to communicate with hardware, and that usually accounts for the 3.2 Gb available memory which people report. I think the onboard vga card will use *some* memory, but probably not a lot, and it may be addressed differently, in which case, it may not have any affect (that's pure speculation on my part!).

I believe to use all of the 4Gb of memory you will need to use either PAE or 64 bit. Also, in my personal case, I have a laptop so disabling the on-board video is not an option for me.

Please post back and let us know how you get on. :)

---

### Post by 73ckn797 on 2009-04-13
The BIOS on my MB has no switch to remap memory. I do not have on-board video either. Using Jaunty 64 bit gives plenty of speed for my needs.

---

### Post by harry70 on 2009-04-13
> **73ckn797 said:**
> The BIOS on my MB has no switch to remap memory. I do not have on-board video either. Using Jaunty 64 bit gives plenty of speed for my needs.

Oh, I just assume onboard video is the rule these days. Well, that's one less potential problem with 64 bit and one less thing to turn off since you're adding a video card.

As far as the rest of the hardware mapped in higher memory, you might double check or look for a bios upgrade. I did a quick search on BIOSTAR TF560 and found this (may or may not be yours):

[http://forums.pcper.com/showthread.php?t=447120&page=3](http://forums.pcper.com/showthread.php?t=447120&page=3)

[[IMG]http://img135.imageshack.us/img135/9529/ram1aq9.th.jpg[/IMG]](http://img135.imageshack.us/my.php?image=ram1aq9.jpg)

(see line 7 setting)

It's only 5%, so no big deal, but if it's just a matter of flipping a bit, it's worth the extra ms saved.

---

