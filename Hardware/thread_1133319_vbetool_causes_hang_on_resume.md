---
title: "vbetool causes hang on resume"
date: 2009-04-22
forum: Hardware
---

### Post by kazzmir on 2009-04-22
When resuming after a suspend, vbetool was hanging causing the entire system to not respond.

I was using 8.04 earlier today then I upgrade to 8.10. Suspend/resume worked fine in 8.04 but when I upgrade to 8.10 I couldn't resume anymore. I tried a bunch of fixes that I found after some googling to no avail. Finally I upgrade to 9.04 and saw the same behavior. Well almost, in 9.04 the first suspend/resume worked (except that I had to press alt+ctrl+f1 to switch to tty1 to force ubuntu to reload x11) but successive suspend/resume's failed.

I noticed after the first resume that 'vbetool' was running. It didn't seem to be getting anywhere so I kill -9'd it. 2 more instances of vbetool started up which I also killed. I then did
$ mv /usr/sbin/vbetool /usr/sbin/vbetool.old

and now I can suspend/resume just fine. vbetool doesn't seem to be doing anything worthwhile.

I have a toshiba satellite a215 s474.

---

