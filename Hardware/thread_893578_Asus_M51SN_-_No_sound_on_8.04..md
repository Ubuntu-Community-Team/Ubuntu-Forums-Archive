---
title: "Asus M51SN - No sound on 8.04."
date: 2008-08-18
forum: Hardware
---

### Post by Ylke on 2008-08-18
So I have the Asus M51SN -notebook and sound drivers aren't working out of the box, and I can't find anywhere any drivers that would work on my laptop. I'm quite beginner so I would like to have as  easy solution as it's possible. :popcorn:

---

### Post by shinyone on 2008-09-13
I know this question is a few weeks old, but I'll post the answer here as it took me a while to track it down.

> **embe83 said:**
> Try adding two lines to /etc/modprobe.d/alsa-base
```
options snd-hda-intel enable=1 index=0 model=lenovo
alias snd-card-0 snd-hda-intel
```

It works for me.

---

