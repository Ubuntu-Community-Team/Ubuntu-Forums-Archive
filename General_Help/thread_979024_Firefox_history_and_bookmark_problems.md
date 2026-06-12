---
title: "Firefox history and bookmark problems"
date: 2008-11-11
forum: General Help
---

### Post by bravo sierra echo on 2008-11-11
Been having a few problems lately so I'll list them all here, in case you think they're linked.

Computer is a no-brand-name box with a 2.4ghz Intel Celeron and 512mb RAM, running 8.04 Hardy.  It has recently taken to completely freezing, requiring a hard reboot.  Sometimes it will run for days quite happily, sometimes you have to reboot three times in a row.  Just once, it's given a CMOS checksum error on startup.

Apparently coinciding with these problems, Firefox 3.0.3 has started acting up.

My bookmarks have all disappeared, and it won't save new ones
Back, forward, reload, and stop buttons have all stopped working (ghosted out)
History has disappeared, and it doesn't save it any more
The address bar doesn't work properly - it doesn't display the current URL, it only displays the last URL I typed in.

Anyone come across this before?

---

### Post by Mr_JMM on 2008-11-11
Could this be a RAM issue? Duff card perhaps.

Do you have any way of testing the RAM cards?

---

### Post by bravo sierra echo on 2008-11-11
I was suspicious of the RAM too, for the freezing, but would it affect Firefox like that?

I was planning to upgrade soon anyway and RAM is so cheap at the moment the best thing might be to just buy a gig and see if it helps...

---

### Post by mrphd on 2008-12-11
Your Firefox profile may have become corrupt. You can fix this by deleting your existing profile (be warned, bookmarks, download history, history, etc. will all be lost)

to do this, open a terminal and type:

firefox -ProfileManager

then delete your existing profile and create a new one.

hope this helps

---

