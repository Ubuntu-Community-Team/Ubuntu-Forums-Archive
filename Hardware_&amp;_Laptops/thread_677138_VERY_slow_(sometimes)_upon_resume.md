---
title: "VERY slow (sometimes) upon resume"
date: 2008-01-24
forum: Hardware &amp; Laptops
---

### Post by chadjohnson on 2008-01-24
Hi, I have an Acer Aspire 5050 (5050-3389, I believe) with Gutsy, and often after resuming from suspend the computer is very slow and almost unresponsive (just as if I had left Windows on for several days). This has also happened once after leaving the laptop idle (not on suspend) for several hours.

Initially suspend and resume were altogether not working, due to a problem with the proprietary ATI drivers. I solved this by recently upgrading to the newest driver (installing manually).

I was also having a problem where the battery indicator was not showing up, but I solved this by updating my initramfs via the process here: [http://ubuntuforums.org/showthread.php?t=609925](http://ubuntuforums.org/showthread.php?t=609925)

I am also running Compiz-Fusion. Additionally, because I'm using an ATI card, I have to have xserver-xgl installed for Compiz-Fusion to work. I did notice today, while experiencing this slowness issue, that XGL was using on average 25% of my CPU, and whenever I switched windows it would often jump up to 100%. This was with desktop effects turned off (but XGL still running).

Furthermore, the harddrive LED is constantly on when this problem is occurring.

Any ideas on how to solve this problem? Is this a known bug?

---

### Post by chadjohnson on 2008-01-28
Bump...anyone?

I removed xserver-xgl...same results.

---

### Post by chadjohnson on 2008-01-30
BUMP BUMP BUMP Please help

My laptop has 1GB of RAM, and I noticed it was using all of the swap partition upon resume. It still does this after resizing the swap partition from 512MB to 1GB.

This is pissing me off...wtf is going on?


*EDIT* Ok, wait, actually it's NOT using all of the swap (it's only using 406.4MB out of 1024MB)...after showing all processes in the System Monitor, I see that mysqld is using like 85%. Something to do with mysql.

---

### Post by phoenix5002 on 2008-01-30
I'm having similar problems as you.  If your having a problem with your computer going to a black screen for like 2min when u turn it on, I fixed that with this suggestion:
[http://ubuntuforums.org/showthread.php?t=681127&highlight=phoenix5002](http://ubuntuforums.org/showthread.php?t=681127&highlight=phoenix5002)

If your talking about suspend and hibernate not working properly then you can try this:
[http://ubuntuforums.org/showthread.php?t=471855](http://ubuntuforums.org/showthread.php?t=471855)
I am currently testing it out, so I don't know if it will work yet, but u can certainly try it.

---

### Post by chadjohnson on 2008-01-30
Thanks for the reply. I think I had that issue with the blank screen on boot (i.e. the splash screen was not showing), but I already fixed that.

The hibernation/suspend issue I had before, where it would not suspend at all, was due to ATI drivers. What exactly does your resolution fix?

---

### Post by chadjohnson on 2008-01-30
> **phoenix5002 said:**
> If your talking about suspend and hibernate not working properly then you can try this:
[http://ubuntuforums.org/showthread.php?t=471855](http://ubuntuforums.org/showthread.php?t=471855)
I am currently testing it out, so I don't know if it will work yet, but u can certainly try it.

Hey! It looks like this may actually be working...thank you.

---

### Post by chadjohnson on 2008-03-08
Just thought I should follow up and inform any future readers that this issue has NOT been resolved, and it has continued to plague me and utterly waste my time. The problem is an incompatibility between the ATI fglrx driver and the new SLUB memory allocator in the Kernel.

See [bug #121653]("https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/121653/") for more details. Oh, and always remember that ATI sucks as it does not give a rat's *** about Linux users.

And if you, like me, are stuck with this ridiculous issue, please go [here]("http://ati.cchtml.com/show_bug.cgi?id=739") and vote for ATI to get off its *** and fix this issue. I highly doubt this will be fixed in Hardy as its kernel also uses SLUB.

---

