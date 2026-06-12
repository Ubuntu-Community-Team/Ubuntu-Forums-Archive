---
title: "Get hardware info?"
date: 2008-10-09
forum: Hardware
---

### Post by dai_vernon on 2008-10-09
How do I determine my exact hardware specifications?  Such as my motherboard model and such?  I am doing OS research and need to know the exact specs...

In OS X there's a system profiler that's a clearinghouse for hardware info.  Is there one here?

---

### Post by cariboo on 2008-10-09
In a terminal type:

```
sudo lshw
```

This will print out all the hardware information you could need and then some.

You do realize that OS X only runs properly on Apple certified hardware so any hardware results are guaranteed to be correct.

Jim

---

### Post by Herman on 2008-10-09
Another command which is also very good for motherboard and BIOS info is this one,
```
sudo dmidecode
```

---

