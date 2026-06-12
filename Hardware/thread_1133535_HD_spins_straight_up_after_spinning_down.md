---
title: "HD spins straight up after spinning down"
date: 2009-04-23
forum: Hardware
---

### Post by ayqazi on 2009-04-23
Hi,

I've got a weird problem that has started happening recently...

I've got 4 HDDs in my computer - 2 are used while I'm Windows'ing, 2 while I'm Linux'ing.  I obviously want the 2 Windows ones to shut up when I'm not using them.

The strange thing is, when I 'hdparm -y' one of them, it spins straight up again!  I've even set a 1 minute sleep time on it, and it doesn't go to sleep any more!

Strangely, shutting down/sleeping works fine under Windows Vista.  The Samsung auto-diagnostic tool also confirmed that spin-up/spin-down works fine.

It used to just fine - but for some reason it doesn't any more.  The oscillation is driving me crazy... anyone have any tips?

The HDD is a SAMSUNG HD103UJ

Thanks

Update: From another forum, I discovered that it was a hdparm issue... version 9.15 fixed it.  Whoopee!

---

