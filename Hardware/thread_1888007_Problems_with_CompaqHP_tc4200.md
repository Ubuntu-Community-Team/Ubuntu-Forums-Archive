---
title: "Problems with Compaq/HP tc4200"
date: 2011-11-28
forum: Hardware
---

### Post by fiddlefye on 2011-11-28
I've been running the most recent version of Ubuntu for a few weeks now and have had constant issues I haven't been able to resolve. Here are the symptoms and where I suspect the issue my stem from. I have no idea how to begin to resolve things, but they are driving me batty.

I have constant darkening of the screen and freezing, accompanied by the HD writing away something quite madly in the background. I am fairly sure it has to do with how the battery level is being recognized/analyzed though it happens equally when plugged into AC. When running on battery sometimes it will show part level and then jump to full and back during one of the episodes when everything darkens and freezes. Before the latest OS upgrade the battery level only showed when either off AC or charging, since then it has been visible full time.

I'm wondering it anyone else has had similar issues and also if there are any potential fixes out there?

Thanks!

---

### Post by fiddlefye on 2011-11-28
I'd also like to note that during those periods when running correctly this version runs very well indeed. I do wish I could get some direction in how to resolve this rather debilitating issue.

---

### Post by Mark Phelps on 2011-12-01
Since this is a laptop, have you notice if the darkening and freezing happens only after the laptop has been on for a while? Or does it happen right after you do a cold start?

If the former, it's likely to be a heat-related issue as the recent kernels packaged with Ubuntu 11.10 have been exibiting this problem.

The only solution at present is to manually roll-back to an older kernel -- but that carries other risks and I don't recommend it.

If the laptop is not getting hot, then sorry, I don't know what is causing the problem.

---

