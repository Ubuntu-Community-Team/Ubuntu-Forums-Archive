---
title: "Question about kernel..."
date: 2008-07-20
forum: General Help
---

### Post by Th3Professor on 2008-07-20
This is, in all seriousness, intended to be asked with a real curiosity for what the future of the Linux kernel might entail.

Does anybody know what the future of the Linux kernel might entail?

Is there any word on Linux kernel version 3 or what it might be like when it runs out of 2.x.etc. numbers?

Thanks!

EDIT:
I should clarify... I mean, by "what it might entail", more specifically what might be planned or "in the works" or similar.

---

### Post by Tim Sharitt on 2008-07-21
Right now it looks like just incremental changes, as for the numbering there has been an discussion on the kernel mailing list about this
> 
Date:	Mon, 14 Jul 2008 19:22:04 -0700 (PDT)
From:	Linus Torvalds <torvalds@linux-foundation.org>
To:	Stoyan Gaydarov <stoyboyker@gmail.com>
cc:	[email]linux-kernel@vger.kernel.org[/email], Alan Cox <alan@lxorguk.ukuu.org.uk>,
	[email]gorcunov@gmail.com[/email], [email]akpm@linux-foundation.org[/email], [email]mingo@elte.hu[/email]
Subject: Re: From 2.4 to 2.6 to 2.7?

On Mon, 14 Jul 2008, Stoyan Gaydarov wrote:
> 
> Second I wanted to talk about the linux 2.7.x kernel, whats in the
> making or maybe even not started

Nothing.

I'm not going back to the old model. The new model is so much better that 
it's not even worth entertaining as a theory to go back.

That said, I _am_ considering changing just the numbering. Not to go back 
to the old model, but because a constantly increasing minor number leads 
to big numbers. I'm not all that thrilled with "26" as a number: it's hard 
to remember.

So I would not dismiss (and have been thinking about starting) talk about 
a simple numbering reset (perhaps yearly), but the old model of 3-year 
developement trees is simply not coming back as far as I'm concerned.

In fact, I think the time-based releases (ie the "2 weeks of merge window 
until -rc1, followed by roughly two months of stabilization") has been so 
successful that I'd prefer to skip the version numbering model too. We 
don't do releases based on "features" any more, so why should we do 
version _numbering_ based on "features"?

For example, I don't see any individual feature that would merit a jump 
from 2.x to 3.x or even from 2.6.x to 2.8.x. So maybe those version jumps 
should be done by a time-based model too - matching how we actually do 
releases anyway.

So if the version were to be date-based, instead of releasing 2.6.26, 
maybe we could have 2008.7 instead. Or just increment the major version 
every decade, the middle version every year, and the minor version every 
time we make a release. Whatever.

But three-year development trees with a concurrent stable tree? Nope. Not 
going to happen.

		Linus
--
To unsubscribe from this list: send the line "unsubscribe linux-kernel" in
the body of a message to [email]majordomo@vger.kernel.org[/email]
More majordomo info at  [http://vger.kernel.org/majordomo-info.html](http://vger.kernel.org/majordomo-info.html)
Please read the FAQ at  [http://www.tux.org/lkml/](http://www.tux.org/lkml/)




---

### Post by sdennie on 2008-07-21
> **Th3Professor said:**
> 
EDIT:
I should clarify... I mean, by "what it might entail", more specifically what might be planned or "in the works" or similar.

The biggest user visible feature is likely to be, "Add support for new hardware".  Most of the features are not intelligible to the majority of people but, to understand "what they might entail", it's probably best to just look at what they have been in the past so you can get an idea of what "kernel features" means.  To see the notable changes in the latest release of the kernel, check [http://kernelnewbies.org/LinuxChanges](http://kernelnewbies.org/LinuxChanges).  To see a list of all the 2.6 kernels and the notable changes between versions, check [http://kernelnewbies.org/Linux26Changes](http://kernelnewbies.org/Linux26Changes).

---

### Post by Vivaldi Gloria on 2008-07-21
Watch 

[http://www.youtube.com/watch?v=L2SED6sewRw](http://www.youtube.com/watch?v=L2SED6sewRw)

to learn more about the kernel development process.

---

### Post by Th3Professor on 2008-07-21
Thanks for the replies, it's much appreciated.

I come from a more Unix background, so the Linux kernel is... uhm... "different". ;)

The whole bit Linus was going on about made very good sense, reminds me somewhat of the Gentoo versions, albeit nothing incredibly original. Yet, it's practical, so originality doesn't matter.

The idea of the date, or year/decade/etc., can go a long ways.

With the rate the Linux kernel goes through changes, perhaps something like 2007.7.21 as the core version reference (not yet including any "-xx" or similar type tags) would be ideal. Simply: Year.Month.Date

I'm curious to see how they actually end up changing the kernel versions reference. :D

---

