---
title: "Update fixed shutdown problem. But how?"
date: 2014-03-12
forum: Hardware
---

### Post by Brian0079 on 2014-03-12
Great and Powerful Oz,

I'm running 12.04 on last year's Acer laptop. Bought it off the shelf so I had to replace Win 8 with Ubuntu myself. Everything worked fine except it got hung up during shutdown, freezing without actually turning off. I had to physically turn the laptop off by holding down the power button. Minor inconvenience. I tried a few solutions found on the forum and elsewhere, as well as doing a complete reinstall, all to no avail. 

I installed the latest round of updates yesterday and TA-DA!, the laptop shuts down perfectly now. 

So my question is, what is in this round of updates that would have fixed the problem? 

I'm an enthusiastic supporter and I've learned quite a bit about Ubuntu and Linux in the last three years but I'm still a noob so talk slowly and use small words. Ha. 

Thanks.

---

### Post by tgalati4 on 2014-03-12
Open a terminal and post the output of:

```
uname -a
```

It's possible that a small patch to the kernel fixed your problem.  You would have to go through the release notes for that patch to determine if that is the case.  Consider yourself lucky!

---

### Post by Brian0079 on 2014-03-12
Thanks tgalati4. What am I looking for in the output? 

And yeah, I'm super grateful. Just really curious what made the change. I assume it had to be some patch with the hardware. I'm a journalist by training so I'm a slave to curiosity.

---

