---
title: "Hard Drive Speed?"
date: 2010-10-10
forum: Hardware
---

### Post by csharpplus on 2010-10-10
How can I tell what is the speed (RPM) of my hard drive? (5400 / 7200 etc)

---

### Post by JustinR on 2010-10-10
> **csharpplus said:**
> How can I tell what is the speed (RPM) of my hard drive? (5400 / 7200 etc)

Its probably easiest just to look at the HDD itself - the sticker on it should tell you everything you would need to know.

---

### Post by csharpplus on 2010-10-10
thanks, but I have a laptop and taking out the HDD is a pain. is there a way to know this by running some shell command?

---

### Post by JustinR on 2010-10-10
> **csharpplus said:**
> thanks, but I have a laptop and taking out the HDD is a pain. is there a way to know this by running some shell command?

Not that I know of - maybe someone else can help.

---

### Post by PresenceofMind on 2010-10-10
What make is this laptop?

---

### Post by sikander3786 on 2010-10-10
I don't think if Linux has got a command like that.

You can use

```
lshw -C disk
```

to find the model no. and then Google it. You may find the HDD specs that way, not directly.

---

### Post by csharpplus on 2010-10-10
perfect -- thank you!

---

