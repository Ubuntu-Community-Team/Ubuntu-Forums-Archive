---
title: "Ubuntu Requiring Re-Install Every Day"
date: 2008-10-08
forum: General Help
---

### Post by UnderTheOath on 2008-10-08
Okay, so I'll install with Wubi. Everything works fine the first two time. Then I'll do something. And Sometimes it's okay and I can fix it, but more often than not I need a complete re-install.

This has been happening for 3 days or so.

No, I love Ubuntu. I'd love to keep using it. And I love what WUbi has to offer. But I can't re-install every day. Besides the fact that I'm losing all my data, it's just damn annoying.

No what the hell is going on? What happens is, Ubuntu just kinda slows down so badly you can't do anything. Sometimes it'll freeze. And then my only option is to reboot. And then, voila! Most often, Ubuntu doesn't work after that. Even if I boot back into XP first and shut down properly. It'll start to load and then freeze up.

Frustrating. What's happening here?

---

### Post by ago on 2008-10-08
You have to run some diagnostics to see where the bottleneck is. It might be that you are out of (virtual) disk space or out of memory and/or swapping a lot or are running some greedy process. Usual commands for that are: df, top, free

Also check on the windows side that the disk is not too fragmented.

---

