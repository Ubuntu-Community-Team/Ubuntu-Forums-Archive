---
title: "AVG anti virus"
date: 2009-08-05
forum: Installation &amp; Upgrades
---

### Post by slatgolf on 2009-08-05
As a newbie can someone show me how to get AVG anti virus up and running on 9.4. I downloaded the AVG deb and installed ok but can't get it to run. I just want the assurance of anti virus up and running.:(

---

### Post by kayvortex on 2009-08-05
Well, the obligatory rant first: you don't need anti-virus in linux. There do exist linux viruses, but none are in the "wild". Some people will prefer to err on the side of caution, but the chances that you'll ever come across one are minuscule. I prefer not to have that level of bloat on my system that all AV programs inevitably carry. So, although I wont tell you not to have an AV program, I'd also say that *I* think it's pointless (although I'm ready to be corrected by someone more knowledgeable).

By the looks of it, don't you simply need to run the program avgctl? Enter into a terminal:

```
avgctl
```

Take a look at its man page to read up on it:

```
man avgctl
```

and press 'q' to quit from it.

---

### Post by slatgolf on 2009-08-05
> **kayvortex said:**
> Well, the obligatory rant first: you don't need anti-virus in linux. There do exist linux viruses, but none are in the "wild". Some people will prefer to err on the side of caution, but the chances that you'll ever come across one are minuscule. I prefer not to have that level of bloat on my system that all AV programs inevitably carry. So, although I wont tell you not to have an AV program, I'd also say that *I* think it's pointless (although I'm ready to be corrected by someone more knowledgeable).

By the looks of it, don't you simply need to run the program avgctl? Enter into a terminal:

```
avgctl
```

Take a look at its man page to read up on it:

```
man avgctl
```

and press 'q' to quit from it.
Thanks i'll try it

---

