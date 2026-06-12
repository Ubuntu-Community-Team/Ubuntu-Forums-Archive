---
title: "Dell XPS m1730 fan question"
date: 2010-01-10
forum: Hardware
---

### Post by dtbaker on 2010-01-10
Hey all,

I have an old Dell XPS M1730 here. The i8k modules are loading fine on boot and all the dellLED etc.. programs work fine, I'm just wondering what others find as normal fan operation?

I didn't realise my m1730 had fans until I played around with the i8kfan tool. The noise from `i8kfan 2 2` gave me a fright, I thought it was taking off. Turns out my fans have always been off, and will stay off until I manually run `i8kfan 1 1`. They don't even spin up on boot like another dells i've seen.

After 10 or so minutes the fans re-set to the off state (ie: i8kfan 0 0) automatically. 

Anyone else notice this? Or do your fans automatically turn on when the load / temperature goes up? 

I think I'm going to run a `i8kfan 1 1` cron job in the background just to be safe. 

Also have flashed the A10 bios and that didn't change anything either.

Cheers heaps,
Dave

---

