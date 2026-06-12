---
title: "Is my SSD failing?"
date: 2016-12-04
forum: Hardware
---

### Post by ArgentWarrior on 2016-12-04
[COLOR=#1D2129][FONT=Helvetica]Is GSmartControl just a POS or is my SSD actually failing? Everything is either "old age" or "pre-failure". The laptop is a Dell V131, and the drive is barely more than a month old. I haven't had any issues with it whatsoever. Also for some reason the temp is always read as 100C, even though I could turn off my laptop now and take it out, and it'll be cool to the touch. My fans aren't even going right now.


[/FONT][/COLOR][IMG]https://transfer.sh/YNLCz/screenshot-from-2016-12-04-08-52-18.png[/IMG]

---

### Post by TheFu on 2016-12-04
SMART data is next to useless. Only a few values are of any real use.  There's an entire science (and superstition) about these values. Every drive is going to fail at some point. That point is really unknown.  I've had drives fail the 2nd day and others have almost 10 yrs constant service.

The only defense against storage corruption and failures is versioned backups.  If the drive failed now, how much data would you lose? How good are your backups?  That's the real question.

---

### Post by kpatz on 2016-12-04
The attribute type is just that, a type.  It indicates if *changes* in the value are indicative of a failure, or old age.  For example, raw read error rate if it starts increasing indicates a possible failure.  In your case that value is zero.  The "old age" values will gradually change as these are normal occurrences that lead to wear and tear over time; for example, load cycle count on a mechanical hard drive or erase count on a SSD.  Usually you'll get an overall pass/fail condition that indicates if the drive is ok or not.  In your case, your drive appears to be fine.  Just keep backups as others have said since any drive can fail at any time.

---

