---
title: "Mouse pointer jumps back to a point every second during some games"
date: 2012-05-02
forum: Hardware
---

### Post by BryanFRitt on 2012-05-02
Mouse pointer works fine for most things, but with some games the pointer keeps jumping back to a spot about every second. It happens with 'Mouse', 'Track Stick', and 'Touch Pad'.


[FONT="Courier New"]lbreakout2[/FONT] - on the menu screen it works fine, but swith over to playing a game it gets jumpy
[FONT="Courier New"]nexuiz[/FONT] - messes up right from the start
[FONT="Courier New"]openarena[/FONT] - messes up right from the start, etc...
(These are just the ones that I tried this out with, there's probably more...)

Update: found this website:
[https://bugs.launchpad.net/ubuntu/+source/unclutter/+bug/61105](https://bugs.launchpad.net/ubuntu/+source/unclutter/+bug/61105)
"stop unclutter before launching a conflicting application."

So you can `[FONT="Courier New"]killall unclutter[/FONT]` first. It's part of `[FONT="Courier New"]kubuntu-full[/FONT]` so if you unintall `[FONT="Courier New"]clutter[/FONT]`, it'll remove the `[FONT="Courier New"]kubuntu-full[/FONT]` meta-package too, if that's installed. Maybe `[FONT="Courier New"]unclutter[/FONT]` should be removed from the `[FONT="Courier New"]kubuntu-full[/FONT]` meta-package grouping?

---

### Post by lee8oi on 2012-11-18
I had that mouse jump problem for so long, I could never find a solution that fixed it. Killing unclutter did it. I removed unclutter, and yes it removed the meta package for kubuntu-full. But that's no problem for me. Thanks for posting this solution. Even looking at that bug page I didn't even catch that.

---

