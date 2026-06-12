---
title: "nivida compiz freeze"
date: 2009-05-21
forum: Hardware
---

### Post by interceptorV8 on 2009-05-21
just to try it out, i enabled the restricted drivers to see if i could get the cool effects on jaunty that i see everyone using on youtube videos.  i got it working, but when the higher graphics/effects are enabled, it works great for a little while and then randomly freezes.  my graphics card is nvidia 7300 gs.  not the greatest, but better than integrated.  

has there been any solutions to the random freezing that myself and others have been experiencing?   OR... is the only solution a better video card?

---

### Post by coffeecat on 2009-05-21
Which were the "higher/graphics effects"? I have used a 7200GS in Jaunty, which is marginally slower than your 7300GS, and compiz was fine. Never had a freeze. I've also tried a 6200 card with a 24" monitor and that was mostly fine. If I selected the "beam up" effect for closing a window, and closed a maximised window, the beam up hesitated a bit, but that's just about it.

Perhaps your card is overheating when it freezes on you. You say it happens when you enable extra effects, so it will be working hard and getting hot. If it's passively cooled, check that you've got adequate case ventilation - perhaps add a case extractor fan if there isn't one. If the card has its own fan, make sure it's not clogged with dust and working properly. What make is the card? Cheap makes tend to use cheap parts - which includes the fan and/or the design of the heatsink.

Another thing to look for: what chipset does your motherboard have and do you have onboard graphics? I was getting some really weird problems with one machine with a nvidia chipset and onboard nvidia (7025) graphics with a PCIe nvidia card using the proprietary nvidia driver. It turned out that the problem was that the BIOS wasn't automatically disabling the onboard video (as most do). When I disabled the onboard video, the problems went away. There were other odd problems in Intrepid with nvidia cards on motherboards with nvidia chipsets, so if your board has a nvidia chipset, that's something to check out.

---

