---
title: "Strange cpu temperature behavior"
date: 2006-11-27
forum: Hardware &amp; Laptops
---

### Post by jgcamp99 on 2006-11-27
Going by touch and lmsensors readings (because lmsensors called my attention to it in the first place).

But my AMD K7 Athlon XP 3200+, when I'm actually using the computer (with at least Firefox/websurfing level activity) is cooler than when I walk away and leave the computer to idle with just the desktop and no screensaver running ?

I surf the web and use the computer, the temperature rarely exceeds 40* C. I close firefox or any application(s) for that matter, leave it running to go do something else and come back 15 minutes or so later and I see the temperature has risen to 44-48* C. I start using it again and the temperature drops below 40* C, like it is right now @ 37* C. I've made sure everything inside is clean of dust bunnies, but this has me perplexed as to why ? I open the box and touch the base of the heatsink and the temp is slightly warmer than when it is after I have used it for a few minutes and I believe it to be running properly again. This is happening with Edgy, never happened with Dapper. I'm thinking this generic kernel isn't right or something in the coding doesn't idle it properly ? I've even installed the athcool program out of the repositories thinking it's an add on that needs to be applied, but no differences in behavior from what I've described.

Anyone else experience bizarre temperature readings ?

---

### Post by jgcamp99 on 2006-11-29
Solved, I got rid of a few programs I normally don't use, clamav antivirus, backuppc and apache webserver. When I went thru the Synaptic Package Manager and started checking off, downloading and installing apps I figured I wanted, I specifically selected clamav and backuppc, but somehow Apache Web Server got installed as well. I uninstalled them completely/permanently and whatever dependencies they had associated with them and now my computer never gets over 39* C under any condition, walk away, use the thing, whatever. And the near 200 MB of memory is now around 140-150 fully loaded at startup configured without those resident applications.

---

