---
title: "Ubuntu Hardy broke my suspend-to-disk after update"
date: 2008-08-30
forum: General Help
---

### Post by Avuton Olrich on 2008-08-30
Hello,

With two completely different computers / installations and completely different hardware configurations suspend-to-disk works as soon as I install Ubuntu Hardy on these computers suspend-to-disk works, but after update it is completely broken (anything >8.04 breaks it).

First thing I do to get some useful information for a bug is to find and try a vanilla kernel which is where I completely wasted a bunch of time and failed. [rant]I cannot believe there is no vanilla kernel package so I can isolate bugs to the crap patches that have been put in Ubuntu's kernel.[/rant] So, I do what Debian guys recommend I do and do make-kpkg with a vanilla kernel which is a complete fail. So, after all the wasted time I just gave up (this was a month or so ago). Also, a Ubuntu kernel git tree would have been awesome as bisection would have taken minutes.

I'm back, a bit refreshed ready to try again to fix this bug, but I really need some direction. Suspend-to-disk works on every other distribution, except for Ubuntu based systems, of course. To reiterate, I really really want to test with a vanilla distribution because I really think there's a really silly patch part of ubuntu's kernel patches as one of my computers I can't find a vanilla kernel that would break suspend-to-disk other then Ubuntu's. Then I could at least file a bug with something useful in it.

Disclaimer: When I say 'Ubuntu' I mean all derivatives, as the same problem occurs on Xubuntu as Ubuntu.

Thanks in advance!

---

