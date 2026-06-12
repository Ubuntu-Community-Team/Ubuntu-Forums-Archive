---
title: "Ubuntu problem, or hardware problem?"
date: 2008-07-21
forum: General Help
---

### Post by carnaka04 on 2008-07-21
A few months ago, I bought a used HP TC1100 tablet from my college (used to be a faculty machine, then they upgraded).  I did a clean install of Gutsy, and everything was fine for a while (except for some VPN issues which seemed to be unavoidable).  After about a month, though, it started going a little goofy.  I boot up just fine, and everything's dandy for n minutes (depending on what I'm doing).  If I open the Gimp, I can expect to get about 20 minutes of work-time.  Firefox or Opera will last about 10 minutes (or less).  Just navigating through folders, looking at pictures, etc, will give me 30-45 minutes of time.  After that interval, however long it is, the machine starts slowing down, very quickly.  Within 2 minutes of that magical threshold, it's absolutely unusable.  If I can manage to get a terminal running 'top', it looks like there aren't any processes that are being particular resource-hogs.  Remote desktop or small games (Mines, Solitaire, etc) are fine, and I can use them for hours (as long as I don't do any of the "bad" programs in the background).  It doesn't seem like a normal RAM failure to me, so I'm hesitant to call it a hardware issue, but I can't think of any reason that Gutsy would act this way.  Before I tear the thing apart testing each hardware component individually, does anyone have an opinion on the diagnosis?

Specs:
512 MB DDR SDRAM
1.1 gHz Pentium M processor
40 gig harddrive
Gutsy Gibbon (7.10)

Thanks.

---

### Post by Potatoj316 on 2008-07-21
It sounds like something is leaking memory, but I dont think that happens too much in Linux.

---

### Post by carnaka04 on 2008-07-21
That was another one of my theories, and it might hold water if one particular program triggered the slowdown (for example, I know Opera can be leaky), but I just can't seem to find any specific program.

I suppose there might be a Gutsy utility that's leaking, maybe from a bad install, but I don't think that would explain why I'm fine on remote desktop or light games.  Any other thoughts?

---

