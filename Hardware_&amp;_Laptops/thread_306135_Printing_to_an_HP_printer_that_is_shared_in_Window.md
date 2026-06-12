---
title: "Printing to an HP printer that is shared in Windows XP"
date: 2006-11-24
forum: Hardware &amp; Laptops
---

### Post by thetictacaddict on 2006-11-24
I've spent a lot of time trying to make this work.  I've read several how-to's in the forums here, and I've been trying off and on for several months to get this working so it's very frustrating that it doesn't.  Maybe someone can offer some insight.

I'm currently running Xubuntu Edgy and I'm trying to connect to a shared printer attached to a computer running Windows XP Home.  I can see the shared printer, but if I try to print a test page, it gets stuck.  The printer makes some noises like it's about to print something, then gets stuck.
I feel like it's taunting me! :evil:

The Windows print queue will show a "Remote Downlevel Document" and get stuck at 64.0KB/SeveralMB.

The printer is an HP PSC1210xi.  It's actually a printer/scanner combo (hence  "PSC" I guess) but I don't care about scanning right now.  I'm using the driver for the 1210 (does not say xi), but I've also tried the 1200 on a recommendation with the same result.  I think they're both the same driver, hpijs, anyway (different versions or settings, though, maybe? :-k ).

Ideas? :confused:

---

### Post by dbbolton on 2006-11-24
i really don't know if it's possible. a friend told me that the print queue files are different in linux and windows.

you could always ditch windows on the other computer ;)

---

### Post by thetictacaddict on 2006-11-24
Not a bad idea!  Unfortunately, it's not my computer and I don't think my family would go for it.  Also, I feel like this should be able to work.  It would be nice, anyway.

---

### Post by thetictacaddict on 2006-11-25
I finally tried plugging the printer into my Xubuntu box, and it worked like a charm (had it installed and printed a test page in a matter of minutes.  much easier than it ever was in Windows).  This is good news: if all else fails I can probably share it from the Xubuntu machine.  However, I would still like to leave it connected to the Windows box for now...

---

### Post by kdawg on 2006-11-25
Not too sure, but doesn't this require using samba to access the shared resource?  I tried this on two machines also, one edgy one xp, and could see the printer, but couldn't print.  Messed with samba and got frustrated, sold printer and bought a hp c6180 with 802.11....  started it up and printed instantly with both computers. Network printing is the way to go.  :)

---

### Post by trubblemaker on 2006-11-29
true true, it is but keeping an eye out there for the windows printer that prints from Ubuntu.

---

### Post by trubblemaker on 2006-11-29
Update [check this out;]("http://ubuntuforums.org/showthread.php?t=32190")

---

### Post by microtodd on 2007-01-07
I had the exact same problem you did.  Printing from Ubuntu 6.10 to a Windows XP shared printer.  The XP queue would show a Remote Downlevel Document stuck at 64.0K.

What worked for me is in Windows XP to go to Control Panel -> Printers and Faxes -> "printer" -> Properties

The go to Ports and uncheck Enable bidirectional support.

That's all it took for me.  YMMV

---

### Post by thetictacaddict on 2007-02-10
> **microtodd said:**
> uncheck Enable bidirectional support.

That fixed it, thank you so much!

I was away at school but I had this thread bookmarked at home, so I checked it.  It is great to have this finally work.

---

### Post by iamah on 2007-09-12
I unchecked and got rid of the message but still doesn't print nothing... not even the led blinks, I think is not getting to the printer...

---

### Post by iamah on 2007-09-12
thanks, that worked

---

