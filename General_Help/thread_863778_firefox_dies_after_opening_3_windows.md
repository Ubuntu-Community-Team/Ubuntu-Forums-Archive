---
title: "firefox dies after opening 3 windows"
date: 2008-07-18
forum: General Help
---

### Post by Just_SomeGuy on 2008-07-18
Odd problem here on a dual core 4 gig ram machine with all updates.

Firefox locks up, grays out, and needs to be force quitted the instant you open 3 windows. 
I can have two up with 50 tabs, or two up with blank pages, but the instant I open the third it locks up.

While this is going on I can use and open every other app just fine so it doesn't seem to be a resource thing.

Any ideas? Anyone else have this problem?

---

### Post by SunnyRabbiera on 2008-07-18
It might be memory load.
Depending on your specs and such.

---

### Post by Just_SomeGuy on 2008-07-18
> **SunnyRabbiera said:**
> It might be memory load.
Depending on your specs and such.

I doubt it. I'm not using much of what I have, and this is a fairly recent phenomenon.

I pulled this before I caused a lockup just now:
Mem:   3367288k total,   923088k used,  2444200k free,

Also, its only firefox. I can open and use very resource intensive apps while firefox is locked up and have no ill effects.

---

### Post by y-lee on 2008-07-18
Does firefox give any errors when you start it from a terminal and it grays out

```
firefox
```

Do you have the same problem with a new profile

```
firefox -P
```

---

### Post by Just_SomeGuy on 2008-07-18
> **y-lee said:**
> Does firefox give any errors when you start it from a terminal and it grays out

```
firefox
```

Do you have the same problem with a new profile

```
firefox -P
```


Both commands return immediately with no errors.
Still the same lockup.
During this time firefox shows 102% (huh?) cpu usage although you wouldn't know it from the snappiness of other apps opened during the lockup. Firefox only reports using 3.6% of the memory during this time.

---

