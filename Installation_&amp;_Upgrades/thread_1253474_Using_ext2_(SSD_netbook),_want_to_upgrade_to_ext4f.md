---
title: "Using ext2 (SSD netbook), want to upgrade to ext4/fresh install?"
date: 2009-08-30
forum: Installation &amp; Upgrades
---

### Post by londonali1010 on 2009-08-30
Hi all...I just need some advice and I haven't found anything specific to my probs...

I am running 9.04 on an Acer Aspire One 110L. I originally installed 8.10 as per [here]("https://help.ubuntu.com/community/AspireOne110L"), which recommended using ext2 filesystem because it was non-journaled and would extend the life of the SSD.

Fast-forward to today...I am considering doing a fresh install of 9.10 when it comes out because I've tinkered LOADS with my system in the last year and I'd like to clean it up. My questions are:
[LIST=1]Does it actually give me any advantage by doing a fresh install?
[/LIST]
[LIST=2]Will I really get an advantage by upgrading straight to ext4? Presumably it's more stable (which I can live without because I backup often) than ext2, but is it faster, what with the journaling? And will it appreciably shorten the lifetime of my SSD? I mean, *really*, is my SSD likely to conk out before my netbook is obsolete and I buy another one anyway? Given that my netbook is my primary 'puter...
[/LIST]
All opinions appreciated!

---

### Post by dandnsmith on 2009-08-30
I think the write methods used by SSDs may be sophisticated enough to survive the proposed usage but will you be able to boot when you have an ext4 fs?

Last time I looked grub wasn't equipped, even if the netbook would cooperate (I'm unsure about that one)

Have you looked at the AA1 forums to see if anyone is talking about it?

---

