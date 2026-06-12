---
title: "Disable touchpad while typing on Aspire S7-392"
date: 2014-03-06
forum: Hardware
---

### Post by gillk on 2014-03-06
Got Ubuntu running on my new Aspire S7-392. It screams. My one and only complaint is that I can't seem to disable the touchpad while typing.

There's no option at all to do this in settings. In fact, there I can only change primary button, double click speed, and pointer speed. I'm guessing this is because the drivers haven't caught up to the hardware yet.

Still, though, I would have expected syndaemon to do the trick. Here's the command I'm running at startup, but it appears to have no effect:

```
syndaemon -t -k -i 2 -d &
```

Any ideas?

---

