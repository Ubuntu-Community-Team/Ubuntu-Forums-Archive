---
title: "DV6000 HP laptop popping sounds through speakers when on battery"
date: 2011-06-14
forum: Hardware
---

### Post by linuxafficionade on 2011-06-14
I get a really strange behavior - when I run on battery the speakers create a popping sound when the mouse is clicked.

Haven't been able to isolate why and from where but it looks like my battery is not being properly recognized or something like that. 

When I click on power management it shows that battery life is "estimating".

When I was running Windoze on this machine I had about 1hr life on the battery so it is not in prime condition.

The Ubuntu Distro is Ubuntu Studio 11, I d/loaded the latest release yesterday.

---

### Post by jerrrys on 2011-06-14
i had a dv6000 that pop on boot and was able to fix it with lowering input levels on mixer

---

### Post by linuxafficionade on 2011-06-14
Which mixer?

I disabled sounds from the Window Theme if that's what you mean.

Bear with me - it's been a while since I've been on Linux.

---

### Post by jerrrys on 2011-06-14
open a terminal and enter **asmixer** and see if that works.  there are other mixers and really don't know which one comes default with ubuntu studio.

---

### Post by linuxafficionade on 2011-06-16
Jerry - that didn't work, it prompted me to install, I did and asmixer still won't run.

I found Pulse Audio Volume control and disabled system sounds - still having the issue.

---

### Post by jerrrys on 2011-06-16
try **alsamixer** in terminal

---

