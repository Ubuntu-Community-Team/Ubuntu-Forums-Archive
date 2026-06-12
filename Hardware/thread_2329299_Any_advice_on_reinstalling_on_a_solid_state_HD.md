---
title: "Any advice on reinstalling on a solid state HD?"
date: 2016-06-29
forum: Hardware
---

### Post by sofasurfer on 2016-06-29
Gonna buy my first SSHD. Is installation of Ubuntu any differant than on a standard hard drive? My normal process is to install a DVD with the OS image on it and just follow the prompts. In some cases I would partition the HD with Gnome before installation. Do these proceedures work the same with a SSHD or is there other things I must be aware of? Also, want your experiences with SSHD and recommendations if you have any.
Thanks

---

### Post by QIII on 2016-06-29
Hello!

Just to be sure of terminology, do you mean SSHD (hybrid SSD/HDD) or SSD (Solid State Drive)?

---

### Post by sofasurfer on 2016-06-29
Woops! That why I come here. I mean SSD(solid state drive). I plan on either a 128 g or 256 g SATA for a desktop. A local PC shop is moving (I/O Software) and they are having a moving sale. Currently 40 percent off.

---

### Post by weatherman2 on 2016-06-29
I have never done anything special (compared to using a hard drive) with an SSD in Ubuntu.  I treat it like a hard drive.  Since Ubuntu 14.04, I think, "trim" (to free up previously used flash cells) happens automatically.  If you look back on past posts, people may recommend tips to try to extend the life of your SSD, but I've never worried about it.  I've never had one "wear out" after years of daily use.  (I do monitor S.M.A.R.T. and you can check to see if the drive's controller thinks you are near the end of its useful life.)

Before you get excited about a big sale on SSDs, keep in mind that the price of these things has been dropping like a rock and will continue to do so.  Check NewEgg and Amazon for comparable prices.  Not all SSDs are equivalent - there are different types, and some are cheaper but may not have as long of a potential life (MLC vs TLC).  Check this out:

[http://www.mydigitaldiscount.com/everything-you-need-to-know-about-slc-mlc-and-tlc-nand-flash.html](http://www.mydigitaldiscount.com/everything-you-need-to-know-about-slc-mlc-and-tlc-nand-flash.html)

I recently bought a cheap 480GB TLC Mushkin drive from NewEgg for $95.  I might not use that in a server, but for an every-day computer why not?  It's still important to make backups of your SSDs and expect them to fail just like a regular hard drive.  In a few years, these things will cost even less and you can just replace them with cheaper/faster/larger drives.

---

### Post by DuckHook on 2016-06-29
> **sofasurfer said:**
> ...recommendations if you have any...You will definitely find the following thread from *oldfred*, our resident SSD/HDD Uber Guru, super useful.

[http://ubuntuforums.org/showthread.php?t=2147295](http://ubuntuforums.org/showthread.php?t=2147295)

---

### Post by Bucky Ball on 2016-06-30
Chuck it in, open Gparted, there it is, just like any other drive. Install Ubuntu.

Much of what needed to be done in the early days of SSD is no longer required. Trim is done automatically now, although some people don't like the way Ubuntu has it set by default and tweak that. (oldfred's instructions linked above are from 2013, a long time in SSD land, and some may be redundant, so I'd check against more recent info and whatever you find out on this thread. oldfred may be able to clarify himself if he spots this thread). ;)

---

### Post by DuckHook on 2016-06-30
> **Bucky Ball said:**
> Chuck it in, open Gparted, there it is, just like any other drive. Install Ubuntu.

Much of what needed to be done in the early days of SSD is no longer required. (oldfred's instructions linked above are from 2013, a long time in SSD land, and some may be redundant so I'd check against more recent info and whatever you find out here. oldfred may be able to clarify himself if he spots this thread). ;)I lifted the reference directly from oldfred's sig, so if it's out of date, then our man has some 'splainen ta do! :lolflag:

Seriously though, I still follow the instructions in that thread with all of my installs and it's never let me down.

---

### Post by sofasurfer on 2016-06-30
Thanks all. I see some good advice here.

---

### Post by sofasurfer on 2016-07-02
I ended up purchasing a Sandisk SSD Plus 240 gig solid state drive. Guy at Best buy said there are no special issues installing and using it. I'll try to do it in the next couple of days.

---

### Post by oldos2er on 2016-07-03
There's no difference in the installation procedure, as was mentioned. But for what it's worth, I only have the root partition on SSD, /home is still on older SATA hard disk. Maybe when SSD prices drop more I will move completely over to it.

---

### Post by Bucky Ball on 2016-07-03
> **oldos2er said:**
> There's no difference in the installation procedure, as was mentioned. But for what it's worth, I only have the root partition on SSD, /home is still on older SATA hard disk. Maybe when SSD prices drop more I will move completely over to it.

Same. / on SSD and all data on a HDD along with /swap. 

I needed to install a virtual machine on my wife's computer over the last couple of days and had the bright idea of using some of the spare space on the 120Gb SSD for it (just as I was about to create a partition on the HDD for it). Why not? As it was, there was only a 20Gb / partition on the SSD and nothing else. I'd never thought of using an SSD for VMs before (never installed a VM to hard drive before!) but works great. :)

---

