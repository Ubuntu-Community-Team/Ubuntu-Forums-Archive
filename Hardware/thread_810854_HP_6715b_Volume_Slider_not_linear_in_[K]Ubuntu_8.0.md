---
title: "HP 6715b Volume Slider not linear in [K]Ubuntu 8.04?"
date: 2008-05-28
forum: Hardware
---

### Post by jaem on 2008-05-28
Hey all,

I just got a new HP Compaq 6715b (RM179UA), and was pleased to see that almost everything worked out of the box (had to use ndiswrapper, proprietary ATI driver - oh well), however, I've had one small issue.  The laptop has a touch slider for volume, and it works fine, however, both the hardware and software volume controls don't behave as expected.  I don't think the response is linear, which makes it really annoying; I can't control it properly with the hardware control, since it goes too fast near the high volume end.  (Note that this isn't just hardware that does this, but it is most problematic on the hardware controls, since it doesn't have as fine-grained control)
lspci gives this:
00:14.2 Audio device [0403]: ATI Technologies Inc SBx00 Azalia [1002:4383]

I imagine this is likely a config issue, but I haven't delved into that part of the system configuration yet, so some help would be appreciated.

Thanks,

Jeff

Update: Found [this]("http://ubuntuforums.org/showthread.php?t=532679") - I'll try it for now, but is this the best solution?

---

### Post by zgornel on 2008-05-28
I'm having the same issue on a HP 6820s. I just use it almost at max and lower the volume of individual applications. As for lspci :```

00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)

```

---

### Post by jaem on 2008-06-03
I can't speak for your model, since it has completely different sound hardware.  However, you can try the link I gave in the update to my first post.  The only change I would make is to select "Master" instead of "PCM" in the sound settings box.

Let us know if it works for you.

---

