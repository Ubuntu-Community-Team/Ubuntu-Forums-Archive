---
title: "How can I watch mouse events as they happen?"
date: 2009-03-08
forum: Hardware
---

### Post by MountainX on 2009-03-08
I want to see mouse clicks (for each button) as they happen (to help me "debug" my mouse settings). 

Is there a way to see a log of each event in a terminal window (or GUI)?

---

### Post by sdennie on 2009-03-08
Use xev.  You'll have to generate your events in it's window and it's painful to use but, it will probably do what you want.

---

### Post by MountainX on 2009-03-08
Thank you! xev is perfect.

---

