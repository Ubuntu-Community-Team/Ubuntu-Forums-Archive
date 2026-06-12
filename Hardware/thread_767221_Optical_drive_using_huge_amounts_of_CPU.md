---
title: "Optical drive using huge amounts of CPU"
date: 2008-04-25
forum: Hardware
---

### Post by davemolloy64 on 2008-04-25
Hi all. I realise that the recent release of Hardy has inundated the forums with support requests, but I simply can't find a solution to this myself, no matter how much I Google.

Essentially, after installing Hardy from the 8.04 RC CD, any use of my optical drive is slow, using much more system resources (CPU) than it ever has on Gutsy (or Windows). I'm looking at a fairly consistent 60-100% on DVDs, 30-60% on audio cds.

The upshot of which is that everything from an optical drive stutters and is unwatchable/unlistenable.

I've narrowed it down to an Ubuntu-specific problem, as i dual boot with Windows XP Professional which suffers no problems. Also, I'm certain it's not a codec or compatiblity issue as reading AVI files from my external USB hard disk is faultless, whereas similar files read from an optical disk suffer stuttery playback and high cpu usage.

I've tried reinstalling libdvdcss, libdvdnav, etc, back when I believed it to be a DVD-related problem. The fact is I'm a little stumped. Other info: It's a HP pavilion laptop (ZV6179EA) running an AMD64 3500+ [2.2Ghz] (so it's 64-bit Ubuntu) with 1gb RAM and 128mb ATI Radeon Xpress 200M. The drive in question is a DVD+/-RW (can't remember or find the manufacturer right now, will update when I can). Oh, and compiz on/off makes no difference.

So, while I realise everyone's likely fed up with Hardy upgrade issues, maybe someone will spot this and know straight away what my problem is! Many thanks in advance!

---

### Post by jiri-j on 2008-04-27
Sorry for my very poor english

I have the same problem, i solved it with installation of older kernel (2.6.23.17)

[http://ubuntuforums.org/showthread.php?t=743621&highlight=slow+DVD](http://ubuntuforums.org/showthread.php?t=743621&highlight=slow+DVD)

---

### Post by davemolloy64 on 2008-04-27
Thanks for pointing me in the right direction!

I didn't install an older kernel myself, as I clicked through a few links in the post you suggested and found a different solution here: [http://ubuntuforums.org/showthread.php?p=4615284](http://ubuntuforums.org/showthread.php?p=4615284)

The problem is with DMA, but it can be solved by changing some of the boot modules. DVD playback is perfectly smooth now, and everything's perfect.

Many thanks!

---

