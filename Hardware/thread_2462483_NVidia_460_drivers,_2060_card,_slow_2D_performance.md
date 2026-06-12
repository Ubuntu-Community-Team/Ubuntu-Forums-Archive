---
title: "NVidia 460 drivers, 2060 card, slow 2D performance especially on 4K monitor"
date: 2021-05-21
forum: Hardware
---

### Post by ariskk on 2021-05-21
I got this config
Ubuntu 21.04
Nvidia 460 drivers on 2060 card (laptop)

The 2D graphics performance (especially browsing with firefox) is slow. On 1080p it is sort of ok (but visibly slower than windows), on 4K it is slower i.e. scrolling is not smooth at all and visible refresh issues.

I always had slow nvidia performance, on my older desktop I had the same issue.

Weirdly enough, on my work macbook pro with ubuntu on parallel desktops, on the same 4K monitor, graphics are faster and smoother than both my PC & laptop installations.

I believe this is how the nvidia graphics driver is, just not well optimized, but any commands to debug & figure out if something is wrong? I don't see anything wrong on "NVidia X Server Settings"

Thanks

---

### Post by Autodave on 2021-05-22
Where did you get the graphics driver from?  Can you give us some specifics on your hardware?  My guess is that your laptop has 2 graphics cards and is not using the nVidia one.

The RTX 2060 is a quite fast card and you should not be having that issue.

---

### Post by ariskk on 2021-05-22
I am using ubuntu's "Additional drivers", I'll try to post screenshots.

Indeed my laptop has 2 graphics cards but it seems it is using the nvidia one. When I disable nvidia power savings , it gets a bit faster but not as fast as I would expect. I.e. I need to disable firefox's smooth scrolling because it becomes slow.

---

### Post by ariskk on 2021-05-22
Screenshots[ATTACH=CONFIG]288525[/ATTACH][ATTACH=CONFIG]288526[/ATTACH]

---

### Post by ariskk on 2021-05-22
It may have been just a firefox issue. 
I've found a fix for firefox, in about:config I've set gfx.webrender.all to true and restarted firefox. Now graphics rendering is much faster and I was even able to enable smooth scrolling. I just want to see how stable it will be.

This is the bug entry where I found the fix: [https://bugzilla.mozilla.org/show_bug.cgi?id=629234](https://bugzilla.mozilla.org/show_bug.cgi?id=629234) (at the end of page)

---

