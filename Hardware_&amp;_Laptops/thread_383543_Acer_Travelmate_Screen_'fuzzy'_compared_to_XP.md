---
title: "Acer Travelmate Screen 'fuzzy' compared to XP"
date: 2007-03-13
forum: Hardware &amp; Laptops
---

### Post by bazzer on 2007-03-13
Hi
Just a grumble really. Don't realistically know where to start looking though. My Acer Travelmate 2490 has a 1280 x 800 screen and I've installed Intel 915 to enable this resolution at 60Hz. So the display is 'correct'. However, I notice that the lines are blurry (looks kinda like it's been anti-aliased) in both horizontal and vertical planes. In XP (it's dual boot) it all seems fine though, which I find a little odd.

Maybe I'm being picky, or imagining it. But if anybody knows where I could start chasing this I'd be grateful for a pointer.

My xorg.conf mentions it's default depth is 24 bit but I'm 90% sure XP says 32 bit. Maybe that's it?

TIA

---

### Post by lordkenyon on 2007-05-02
> **bazzer said:**
> Hi
Just a grumble really. Don't realistically know where to start looking though. My Acer Travelmate 2490 has a 1280 x 800 screen and I've installed Intel 915 to enable this resolution at 60Hz. So the display is 'correct'. However, I notice that the lines are blurry (looks kinda like it's been anti-aliased) in both horizontal and vertical planes. In XP (it's dual boot) it all seems fine though, which I find a little odd.

Maybe I'm being picky, or imagining it. But if anybody knows where I could start chasing this I'd be grateful for a pointer.

My xorg.conf mentions it's default depth is 24 bit but I'm 90% sure XP says 32 bit. Maybe that's it?

TIA

I just installed 7.04 and finally (big PITA) got it set to 1280 X 800 on my Aspire 2010 and am having the same issue as you are.  

So any help would be appreciated.

---

### Post by jjordan on 2007-05-03
Search for i915resolution.  Most likely your screen is not actually running at 1280 X 800.  There are several threads addressing this issue (it is a video BIOS thing) and a pretty well written howto.

-j

---

