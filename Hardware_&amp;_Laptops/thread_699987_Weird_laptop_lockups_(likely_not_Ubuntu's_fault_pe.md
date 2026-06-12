---
title: "Weird laptop lockups (likely not Ubuntu's fault per se)"
date: 2008-02-17
forum: Hardware &amp; Laptops
---

### Post by Phil Urich on 2008-02-17
I installed Ubuntu (well, Kubuntu to be specific, but this problem seems unconnected to the specific desktop environment) on a laptop for my sister awhile back, when Vista had just come out and retails stores were foolishly clearancing XP-based machines (it was *cheap*).  It seemed in some ways like this laptop (an Acer Aspire 9402WSMi, 17" screen) was made with installing Linux in mind; it had a small boot partition, then a Fat32 partition with WinXP installed, then an equal-sized empty partition taking up the rest of the space.  Risk free!

So I installed Kubuntu and my sister has been quite happy with it since.  Only problem is, from time to time it freezes, but in a rather odd way; the mouse still works, windows can usually be moved around, but no real interaction (like scrolling down within a window, for example) can be done until it unpauses, perhaps a half-minute later.

I'm pretty sure I've found the error message, though I'm unsure of what it means...but if I leave a console session open and switched to (like starting a new one via ctrl-alt-F5 or whatever and just logging in there and waiting) it starts spitting out stuff like this:

[ 4996.269197] ata1.01 exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2 frozen
[ 4996.269265] ata1.01 cmd a0/00:00:00:00:20/00:00:00:00:00/b0 tag 0 cdb 0x1e data 0

Obviously the time varies, heh, but it's always a pair of those lines close together.  The last three entries on the second line vary, for example sometimes instead of "0x1e data 0" it's been "0x25 data 8 in" or "0x43 data 12 in" or so forth.  

Of course neither my sister nor I have felt like booting into Windows, really ;) but from tiny expeditions, and from one of my friends being a creature of habit and insisting on trying to use Windows the other day on the laptop, we're pretty sure that the problem is in Windows as well; still, it's the Linux part that we want working and I figure hoping someone here knows what's going on is a better bet than trying some Windows forum ;) Plus, the only lead I have is the error message from Ubuntu, after all.

It isn't terribly crucial since she has an eeePC now for when she's actually out and about or at university, but it'd be nice.

---

### Post by Phil Urich on 2008-03-09
Okay, confirmed that it does **NOT** do this in Windows....

---

