---
title: "Laptop buying advice: graphics cards"
date: 2011-08-20
forum: Hardware
---

### Post by oldmankit on 2011-08-20
Hi,

I've never bought hardware with Linux specifically in mind; I also know very little about processors and graphics cards.  So advice is really appreciated.

I've found some acer laptops that I like but would like to know how compatible they will be with Ubuntu.  I use ubuntu for everything, but will probably crank up windows for the odd game.

First I was interested in the Intel i5 processor, but the models I can see all have the NVIDIA GeForce GT 540M graphics card.  I've read that Linux users have had big problems with anything with Optimus technology (e.g. [http://ubuntuforums.org/showthread.php?t=1699939]("http://ubuntuforums.org/showthread.php?t=1699939")).  If I understand correctly, the best a linux user can hope for is to disable it so that it's not draining power.

I looked for AMD processors instead.  The better ones I have seen in my price range (A6-3400M and a8-3500M) come with AMD Radeon HD 6***G2 graphics, using "dynamic switchable graphics technology".  I've searched but haven't found anything conclusive on this (though it doesn't look hopeful).

I'm quite confused about what to get.  I suppose my requirements are:
[LIST]
[*]The ability to use the full Unity interface smoothly (my current laptop is too slow) but otherwise no 3D requirements in Ubuntu. But I want a fast processor with multiple cores/threads for 2D graphics work
[*]If Ubuntu isn't using a piece of hardware, I absolutely don't want it draining the battery 
[*]For gaming, I can use windows
[/LIST]

If anyone can help me with some recommendations I'd be really grateful.  It doesn't have to be an acer laptop.

Thank you.

---

### Post by oldmankit on 2011-08-20
Bump

---

### Post by aeronutt on 2011-08-20
I have a Dell Vostro, with Intel i3 and AMD HD6630M graphics. So far, the AMD graphics card is useless; yes, I power it down to save battery life. i'd love to be able to turn it on as needed, but so far, no luck. I'm HOPING someday AMD will support the 6630 in their proprietary s/w, but not yet. Or, not as good, have vgaswitcheroo work with open source drivers. But again, at least I have not been able to make this work.

---

### Post by oldmankit on 2011-08-21
> **aeronutt said:**
> I have a Dell Vostro, with Intel i3 and AMD HD6630M graphics. So far, the AMD graphics card is useless; yes, I power it down to save battery life. i'd love to be able to turn it on as needed, but so far, no luck. I'm HOPING someday AMD will support the 6630 in their proprietary s/w, but not yet. Or, not as good, have vgaswitcheroo work with open source drivers. But again, at least I have not been able to make this work.
Thanks a lot for your comment.

I'm now looking at the AMD A8-3500M processor with AMD Radeon HD 6640G2 graphics.

That looks pretty close to the card you mention, so I suppose I can expect the same as you.  To be honest with you, I don't mind powering it down since it will save batteries and I don't normally want it running.  I probably only want it for running games (under windows).

Is it easy to power down?

---

### Post by realzippy on 2011-08-21
You do not need dedicated graphics at all (for ubuntu).
..the integrated graphics core of an I3 runs circles
around an ati device driven by the free ati-driver.
Don 't know how it performs with games in windows...

---

### Post by linuxuser12345 on 2011-08-21
Asus laptops seem to be pretty compatible with Ubuntu. You can also try System76: They make their laptops specifically to run Ubuntu on, so you get 100% compatibility, all the time.

---

### Post by SeijiSensei on 2011-08-21
Having chosen to avoid Optimus-based laptops, after a decade of using NVIDIA products for their prior Linux-compatibility, we bought my daughter an [HP dv6tse]("http://www.shopping.hp.com/series/category/notebooks/dv6tse_series/3/computer_store") with an upgrade to the ATI Radeon 6770M graphics card.

To begin with, HP's support for this card was lacking even in Windows!  It wasn't really possible to tell the machine to switch from one adapter to the other except in some limited ways.  That was all fixed in the most recent BIOS update.  Now my daughter can play games with the ATI chip in Windows, and use the Intel chip for everything else.  In Linux, once the BIOS was updated, Ubuntu sees the ATI card and running the "Additional Drivers" application installs the correct proprietary driver.  I haven't figured out how to switch back to the Intel adapter on-the-fly, though. Our Ubuntu installation runs on the ATI card all the time.

Overall we're pretty happy with this machine.  It's a touch heavy, especially in comparison to the ASUS 1201N netbook she was using, but the screen is excellent, and the workmanship feels solid, which hasn't always been the case with recent HP machines.

I'd agree, though, with realzippy's observation that the Intel adapter is perfectly adequate for most tasks.  That wasn't true when we tried playing *Dragon Age: Origins* in Windows.  It wouldn't run on the highest settings using the Intel chip, but it does with the ATI adapter.

---

### Post by Stubby Holders on 2011-08-22
I planned to buy a laptop but I haven't choose a brand, I chose 3 brands which are Samsung, Sony and Dell. What do you think is the best laptop among the three brands?

---

### Post by aeronutt on 2011-08-22
> **oldmankit said:**
> ...
Is it easy to power down?

Yep, a few lines in rc.local and blacklist.conf and all is good. My battery current was cut by almost half when I did this in 11.04. 11.10(alpha) isn't showing the same gains ...yet, but it's alpha.

In /etc/rc.local add:
 modprobe radeon
 echo OFF > /sys/kernel/debug/vgaswitcheroo/switch

In /etc/modprob.d/blacklist.conf add:
 blacklist radeon

I'm not even 100% sure the rc.local edit is needed..but that's what works for me.

---

### Post by amites on 2011-08-22
Save yourself trouble and go with ATI

the Linux support for their cards is excellent

Nvidia works though not as effective - and with fewer config options

luckily these days most of the old school hardware issues have become non-issue

my $.02

---

### Post by oldmankit on 2011-08-23
> **SeijiSensei said:**
> Having chosen to avoid Optimus-based laptops, after a decade of using NVIDIA products for their prior Linux-compatibility, we bought my daughter an [HP dv6tse]("http://www.shopping.hp.com/series/category/notebooks/dv6tse_series/3/computer_store") with an upgrade to the ATI Radeon 6770M graphics card.

To begin with, HP's support for this card was lacking even in Windows!  It wasn't really possible to tell the machine to switch from one adapter to the other except in some limited ways.  That was all fixed in the most recent BIOS update.  Now my daughter can play games with the ATI chip in Windows, and use the Intel chip for everything else.  In Linux, once the BIOS was updated, Ubuntu sees the ATI card and running the "Additional Drivers" application installs the correct proprietary driver.  I haven't figured out how to switch back to the Intel adapter on-the-fly, though. Our Ubuntu installation runs on the ATI card all the time.

Overall we're pretty happy with this machine.  It's a touch heavy, especially in comparison to the ASUS 1201N netbook she was using, but the screen is excellent, and the workmanship feels solid, which hasn't always been the case with recent HP machines.

I'd agree, though, with realzippy's observation that the Intel adapter is perfectly adequate for most tasks.  That wasn't true when we tried playing *Dragon Age: Origins* in Windows.  It wouldn't run on the highest settings using the Intel chip, but it does with the ATI adapter.
Thanks aeronutt for the tips on powering it down.

I've found some Lenovo laptops which might suit.  The G470 has an i5 processor and an AMD Radeon HD 6370M, and although I haven't heard anyone saying this particular card works with Linux, other series 6*M ones do.  As SeijiSensei described.

---

### Post by www.rzr.online.fr on 2011-10-12
> **oldmankit said:**
> 
I've found some Lenovo laptops which might suit.  The G470 has an i5 processor and an AMD Radeon HD 6370M,


If only it had a decent BIOS

-- 
[http://rzr.online.fr/q/lenovo](http://rzr.online.fr/q/lenovo)

---

