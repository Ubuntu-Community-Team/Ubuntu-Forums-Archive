---
title: "How can I know which process is using my HD?"
date: 2007-06-21
forum: Hardware &amp; Laptops
---

### Post by Nightfall on 2007-06-21
Hello,
I'm working on my laptop on OpenOffice writer.
Every now and then I can hear the hard disk working for half a second:

It works half a second then stops some seconds.
It works half a second then stops some seconds.
It works half a second then stops some seconds.
It works half a second then stops some seconds.

... and so on.

How can I see which process is doing this?
This is a problem even because when I'm working on battery, these continuous accesses to hd don't let the hd to spin down and save power.

Help me please!

Thanx a lot.

---

### Post by odiseo77 on 2007-06-21
hmmm, maybe OOwritter is automatically saving your document on a temporal file in your HD to make sure it will be recovered in case of a power failure or system crash??
Anyway, I don't know if this is exactly what you're looking for, but you could try:

```
ps -aux
```

to see which process(es) is(are) using your CPU at the moment you hear the noise.

You can also try:

```
top
```

---

### Post by Nightfall on 2007-06-21
Thank you for helping!
Surely it's not a problem related to OOwriter or to automatic savings: this trouble happens even if I'm not working with OO.org
I tried with top, but I can't relate any process to those disk accesses :-(

---

