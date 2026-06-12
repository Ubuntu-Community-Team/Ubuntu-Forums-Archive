---
title: "Want a New Laptop: Thinkpad Edge Core i-5 Sandy Bridge &amp; Intel HD Graphics 3000"
date: 2011-09-03
forum: Hardware
---

### Post by sadams on 2011-09-03
Hi,

I would love some help with this.

I have read a number of threads here and articles on the web (e.g. [http://phoronix.com/forums/showthread.php?53296-Intel-Sandy-Bridge-On-Ubuntu-11.04-Is-Still-Troubling](http://phoronix.com/forums/showthread.php?53296-Intel-Sandy-Bridge-On-Ubuntu-11.04-Is-Still-Troubling))

regarding the ability of the latest/recent Ubuntu releases to run happily on the most recent Intel Core i-5 Sandy Bridge CPUs and graphics (Intel HD Graphics 3000)

I am looking at this:
[http://uk.insight.com/en-gb/productinfo/laptops/LENYAZ33LU](http://uk.insight.com/en-gb/productinfo/laptops/LENYAZ33LU)
Lenovo ThinkPad Edge E520 1143
Processor - Intel Core i5 2410M / 2.3 GHz ( 2.9 GHz ) ( Dual-Core )
Graphics Controller - Intel HD Graphics 3000 Dynamic Video Memory Technology

I am frustrated that I can't seem to find clear and authoritative guidance from Ubuntu (or indeed via these forums) about whether this CPU/Graphics combination is a viable option to run a recent Ubuntu release.
I can find this: [http://www.ubuntu.com/certification/hardware/201103-7447](http://www.ubuntu.com/certification/hardware/201103-7447)
which is for a similarly named model - but a different chipset.
I see some howtos and guides which suggest workarounds and "fixes" and methods to get certain things working... but it's hard to be confident enough to spend money!

Further there seems to be no clear statement as to WHEN to expect an  Ubuntu release which will happily work on this platform.

It seems crazy to me that this question appears so hard to answer... i.e. "Will this new Laptop with recent decent H/W config work well with Ubuntu?"
If I can't make a confident choice - how can people with little/no relevant expertise/experience?

Some Context:
I'm a long-time Linux user and Ubuntu convert since Warty - running various flavours on various configs (desktops, laptops, MythTV) and have converted a number of family/friend laptops over the years. I'm pretty experienced and have a reasonable understanding of Linux and the various stacks/dependencies required to support H/W components.
Apologies if I have missed something obvious somewhere - please just point me at it and forgive my idiocy :)

Can I buy that laptop and have a reasonable chance of it running well?

Thanks in advance for any help :)
Steve.

---

### Post by sadams on 2011-09-05
Bump!
I was hoping for some advice - or possibly at the least some reassurance/verification that my understanding of this issue is up to date and reasonably sound.

I want to buy a (new, well spec'd, mid-price) thinkpad/laptop... I want to run Ubuntu... I want to have some confidence that I have a good chance of a decent experience if I spend my money... 

Anyone out there know this issue well and able to offer a few lines of advice?
Is this covered well elsewhere by Ubuntu/Canonical - links???

I know it's *MY* issue right now - but I am genuinely shocked at how hard it is to get a feel for this prior to buying a laptop.
We lived with this 10,6, even 3 or 4 years ago... but it's 2011 now and it seems as hard as ever to do decent due diligence  before spending money on a laptop :(

If I can't get help/guidance/commiseration here.... where can I? :\

Steve.

---

### Post by gordintoronto on 2011-09-05
Part of the problem is that manufacturers often change components without renaming the computer. So one Lenovo E520 might have an ABC-1011 ethernet adapter, but another one have an XYZ-99 ethernet adapter. As well, a "model number" might mean a broad range of systems, with optional CPUs, memory and hard drives.

Is it possible for you to take a LiveCD to the dealer, and boot from it on the computer you are considering buying?

When I Googled: lenovo e520 linux
I got quite a few results, including several forum posts marked solved.

It appears the E520 has "switchable graphics" which still has some rough edges in Linux, as far as I am able to determine.

---

### Post by Bucky Ball on 2011-09-05
Sorry but don't think you looked too hard. This took a second to find with 'lenovo e520 ubuntu':

[http://www.ubuntu.com/certification/hardware/201103-7447](http://www.ubuntu.com/certification/hardware/201103-7447)

Sure the card reader can be tweaked to work by now. Here are some more to dig through:

[http://www.google.com.au/#sclient=psy&hl=en&source=hp&q=lenovo+e520+ubuntu&pbx=1&oq=lenovo+e520+ubuntu&aq=f&aqi=g1g-b1&aql=&gs_sm=e&gs_upl=1303l5591l0l5837l12l10l0l0l0l1l387l2565l2-6.3l9l0&bav=on.2,or.r_gc.r_pw.&fp=121f6bf5f6f89279&biw=1368&bih=576](http://www.google.com.au/#sclient=psy&hl=en&source=hp&q=lenovo+e520+ubuntu&pbx=1&oq=lenovo+e520+ubuntu&aq=f&aqi=g1g-b1&aql=&gs_sm=e&gs_upl=1303l5591l0l5837l12l10l0l0l0l1l387l2565l2-6.3l9l0&bav=on.2,or.r_gc.r_pw.&fp=121f6bf5f6f89279&biw=1368&bih=576)

;)

---

### Post by sadams on 2011-09-05
Thanks for the replies:

@gordintoronto
I'm not in any doubt as to the cause of the confusion 
(e.g. "Part of the problem is that manufacturers often change components without renaming the computer")
Given that the problem is tricky I'm looking for an authoritative statement from someone who can help.
I'd be happy with statements about the chipset/graphics in general if that helps - forget the specific Thinkpad model (ref: the phoronix link I posted originally).

@Bucky Ball
*assuming you are not trolling and just made a genuine mistake :)
re: "Sorry but don't think you looked too hard. This took a second to find with 'lenovo e520 ubuntu"
My thread is clearly posted with this in the subject: "Core i-5 Sandy Bridge & Intel HD Graphics 3000" and I state the specs again in the post body and I even link to a page with full specs - I even tagged the thread with those keywords.

You however have linked to an old/stale page for a different chipset/graphics from the previous generation of hardware :(
Ref: Intel(R) Core(TM) i3-2310M CPU @ 2.10GHz
& Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller
Chastising ME for not trying hard enough seems a bit unfair!

I promise you I have looked pretty hard before bothering the forum with my plea for help.

Is there anyone out there who can speak with authority on this?
Can we Ubuntu users adopt these (Core i-5 Sandy Bridge & Intel HD Graphics 3000) most recent architectures and live reasonably happy lives?

Cheers, Steve.

---

### Post by foresthill on 2011-09-05
I run a Gateway with i5 2410 and intel 3000 graphics. It's a model NV57H26u.

All 4 cores are recognized in Ubuntu 11.04, and used more or less constantly. I run Quake 3 on the Intel 3000 graphics in 1024 x 768 and get excellent framerates. 

I'm not sure if one or more of the cores assists with graphics, but I have an older laptop with a Core 2 Duo and Intel 4500 graphics that doesn't run the game nearly as fast.

All I can say is, on my laptop, everything works without any tweaking. During installation, I may have had to use "ACPI=off" to get the installation to finish, but the machine has been a dream running 11.04 so far, compared to the nightmare it has been to get 11.04 working on my other 2 systems.

YMMV, but for me, everything is working great.

---

### Post by sadams on 2011-09-05
@foresthill

Thanks for contributing :)
Interesting & promising...
I find it really hard to be confident about splashing the cash on something when there are such conflicting reports. I understand that different laptop vendors/models/versions may introduce varieties of problems/bugs/features...
however your excperience suggests that in general the chipset/Graphics are fine.

There I was just starting to convince myself to save a hundred pounds (£) and buy a slightly older AMD Fusion based laptop... and now I'm thinking about that core-i5 again.... ;-)

sigh...
Thanks again for taking the time to post :)

Steve.

---

### Post by foresthill on 2011-09-05
My machine was cheap. I paid $449.00 for it at Best Buy. Gateway always seems to give you the most value for your money, or at least they do here in the US.

I saw a Quad Core AMD machine for about the same price, but I like Intel chips since they tend to run cooler.

---

### Post by jbgrzy on 2011-09-10
I just thought I should pipe in here.

I have a e520 with the exact processor you mention. (The Sandy Bridge) Just yesterday I installed Ubuntu on it alongside the preinstalled Windows 7. Everything worked surprisingly well, compared to the experience I had a couple years ago. The only problem I had was with the WiFi card. For some reason it wouldn't show any wireless connections. However, after applying this fix (taken from another thread):

$ rfkill list all
$ sudo rmmod -f acer_wmi
$ sudo rfkill unblock all
$ sudo su
# echo "blacklist acer_wmi" >> /etc/modprobe.d/blacklist.conf
# exit


After that, everything worked fine.

If you have any more questions about this, feel free to PM me with them.

Thanks,
jbgrzy

---

### Post by sadams on 2011-09-10
Hi jbgrzy,
Thanks for contributing.
That sounds positive... can you kindly let me have the exact/specific model number of your thinkpad?

I'll need to make my mind up soon!

Thanks again for taking an interest,

Steve.

---

