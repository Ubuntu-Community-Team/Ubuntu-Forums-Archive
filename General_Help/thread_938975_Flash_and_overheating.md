---
title: "Flash and overheating"
date: 2008-10-05
forum: General Help
---

### Post by benzjehh on 2008-10-05
Hi

I've recently installed Ubuntu on my Dell laptop ( brand new, fan is clean ), and I installed flash with Firefox. When I watch a youtube movie or just open a flash animation the temperature starts rising ( from 40&#730;C to 70&#730;C ) and the CPU usage is nearly at max. How can I fix this?

---

### Post by LoneWolfJack on 2008-10-05
check the system monitor (system->administration) for the applications that have significant CPU load while watching a video. perhaps some other application is draining your CPU power.

what kind of processor do you have?

---

### Post by benzjehh on 2008-10-05
My processor is C2D 8100. It is Flash / Firefox 100%.

---

### Post by cariboo on 2008-10-05
What version of flash are you using, version before 10 are pretty buggy. To find what version of flash you are using open up Firefox and in the address bar type:

```
about:plugins
```

You may have to install a newer version by hand. Search the forums using google as there are plenty of flash installation howtos.

Jim

---

### Post by LoneWolfJack on 2008-10-05
are you using x32 or x64 ubuntu?
do you _always_ have that problem or just periodically?

---

### Post by benzjehh on 2008-10-05
Flash player version: 9.0.124.0

I installed flash from Adobe's site and with Firefox ( automatic install ). Ubuntu version is 32bit and the problem appears at every flash animation / video ( site where flash is required ).

---

### Post by LoneWolfJack on 2008-10-05
you could try one of the howtos and install flash 10. you may also try your luck with gnash (through add/remove apps).

sadly, the flash player in general leaves much to be desired.

---

