---
title: "only getting one-way sync with gcaldaemon"
date: 2008-10-17
forum: General Help
---

### Post by Howlin' Hobbit on 2008-10-17
With Dapper Drake I could only get a one-way sync between Evolution and Google calendar, that being *from* Google *to* Evolution.

I've since gotten a faster computer and installed Hardy Heron. I decided after reading around that I'd try gcaldaemon and installed it. Now I'm getting a one-way sync in the *other* direction, that is to say, I can enter stuff into Evolution and it'll appear on Google calendar but *not* vice-versa.

Anybody else experienced this? I'm pretty sure I followed the directions on the gcaldaemon site properly.

What am I missing?

---

### Post by FokkerCharlie on 2009-05-10
Hi HH

Did you ever find a solution for this?  I am seeing the same issue here.

Cheers
Charlie

---

### Post by Howlin' Hobbit on 2009-05-10
You know the old tech support joke about "is it plugged in?" Or turned on...

I needed to go into my Sessions menu and make sure that gcaldaemon was set to run automagically on startup.

Upshot: If you follow the direction re: what to put where in the config, *and* make sure that gcaldaemon gets running, it should work.

---

