---
title: "Computer slow after disk check"
date: 2010-06-14
forum: Hardware
---

### Post by sripplinger on 2010-06-14
I'm not 100% confident in this connection, but it seems like my computer has gotten really slow since an automatic disk check sequence during boot up.  The hard drive has been spinning almost constantly and one of my cores has just been going 100% the whole time.  Any thoughts on what I could do to figure this out and fix it?

---

### Post by sdennie on 2010-06-14
The output of the following command might be useful:

```

top -b -n 1 | head

```

That should tell you what is eating a core.  It's entirely possible that some process that happens "once in a while" is running and it's not at all related to your disk check.

---

### Post by sripplinger on 2010-06-18
It seems like virtuoso-t was taking up a lot of IO and making my HDD spin a lot.  I turned off the nepomukserver and things seem to be running just fine right now. (This is a KDE specific issue)

---

