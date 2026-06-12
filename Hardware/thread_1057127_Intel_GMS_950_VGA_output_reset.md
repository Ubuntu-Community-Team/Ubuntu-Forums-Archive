---
title: "Intel GMS 950 VGA output reset?"
date: 2009-02-01
forum: Hardware
---

### Post by SamG22 on 2009-02-01
Hi there,

I have an extremely frustrating situation with my aspire one, where if the external screen (a 19" Samsung) resolution - via VGA - is set to 1024 or above, it will occasionally and for no apparent reason go blank.

The graphics chipset in my netbook is an intel GMS 950, and the specs page over at Intel say it should be more than capable of outputting more than I'm asking for.

Until recently the only way I could fix the problem was by putting the laptop into standby, and then waking it immediately at which point the internal screen would restart as well. It may be worth noting I have the inbuilt laptop screen turned off.

Researching earlier today I found out about xrandr, and working blind the last time the screen reset, I tried

xrandr --output VGA off

followed by

xrandr --auto [this turned the laptop screen back on]

and then

xrandr --output VGA mode 1024x768

This made the external screen flicker and reset, but it reset back to a completely b-ARGH IT HAPPEBED AGAIN

...a completely black/tan/dirty white screen. Now I have to restart again so I can see what the hell I'm doing, so please bear with me.

It appears, since I was working on 800x600, that this isn't restricted to 1024 and above, The only external resolution to work so far has been the one suggested by Screen Resolution, which was something like 800x648.

Any help massively appreciated, it's driving me up the freeaking wall.

---

