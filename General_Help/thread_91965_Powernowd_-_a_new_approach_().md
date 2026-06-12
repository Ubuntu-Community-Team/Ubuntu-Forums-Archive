---
title: "Powernowd - a new approach (?)"
date: 2005-11-18
forum: General Help
---

### Post by magnusbb on 2005-11-18
I have an Acer Travelmate and the CPU frequency scaler daemon Powernowd is a must for me. My computer gets very hot when running at full speed hour after hour. Therefore, cpufreqd with it's AC full power policy is not what I want.

But I would like some more speed. I like the default behavour of Powernowd; that is, when the CPU usage rises over 80% it automatically jumps to the maximum CPU level, and then decreases by 200 mhz every second (or something like that).

But I want it to stay a little bit longer "on top". When reaching the maximum frequency I would like powernowd to stay there for minmum a minute or two. It shouldn't go down as early as it does. 

I don't know what Windows XP does, but it has a good policy on this. And I feel there, that I get most out of my computer, but at the same time, "keeping it cool", if you understand.

Can this be done, by scripting powernowd, or do I simply have to use another daemon?

---

