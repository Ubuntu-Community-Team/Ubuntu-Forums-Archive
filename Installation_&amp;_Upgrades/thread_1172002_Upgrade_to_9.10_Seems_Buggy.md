---
title: "Upgrade to 9.10 Seems Buggy"
date: 2009-05-28
forum: Installation &amp; Upgrades
---

### Post by magicdanw on 2009-05-28
After a month or so of the upgrade button tempting me, I decided to finally click it.  I read online in multiple reviews that the new version was faster and smoother running than 8.10, but this does not seem to be the case.  The overall system seems to be slow, applications freeze up or refuse to quit, etc.

Does anyone have any idea what causes this, and how to fix it (short of a fresh install, since I'd rather not if there's an alternative to the whole backup and reinstall bit)?

---

### Post by Steelmourne on 2009-05-28
Don't you mean 9.04? 9.10 should be released sometime in October.

---

### Post by magicdanw on 2009-05-28
> **Steelmourne said:**
> Don't you mean 9.04? 9.10 should be released sometime in October.

Oops, my bad.  I always get the version numbers mixed up.  Oh, and now I can't even play minesweeper anymore due to glitchy graphics!  It's a travesty! ;)

---

### Post by raymondh on 2009-05-28
Hello Magicdanw,

This is the link for the 9.04 release notes.  On the right side (#4) are topics regarding issues.  This is a good place to start the troubleshooting....

[http://www.ubuntu.com/getubuntu/releasenotes/904](http://www.ubuntu.com/getubuntu/releasenotes/904)

Also, would you post (and wrap in code .. to make it manageable) the output of




Regards,

---

### Post by magicdanw on 2009-05-28
> **raymondhenson said:**
> Hello Magicdanw,

This is the link for the 9.04 release notes.  On the right side (#4) are topics regarding issues.  This is a good place to start the troubleshooting....

[http://www.ubuntu.com/getubuntu/releasenotes/904](http://www.ubuntu.com/getubuntu/releasenotes/904)

Also, would you post (and wrap in code .. to make it manageable) the output of




Regards,

I'll check that page out, for sure.  But what did you want to see the output of?

Edit: I took a quick skim through the known issues, and none of the ones that cause lockups or performance issues seem to apply.  I'll take a closer look in the morning, perhaps.  Good night!

---

### Post by raymondh on 2009-05-28
> **magicdanw said:**
> I'll check that page out, for sure.  But what did you want to see the output of?

Edit: I took a quick skim through the known issues, and none of the ones that cause lockups or performance issues seem to apply.  I'll take a closer look in the morning, perhaps.  Good night!

Sorry, had a power outage and decided to go to sleep :)

Let's try with the first issue.  Kindly describe with as much details as possible and what steps have you taken so far.  Also, while you're at it, kindly re-post the output for

```
lspci
```

Thanks and regards,

PS.  The freeze (if you wish to start with that one), is it global (for all apps) or would it be limited?  If so, which apps?  When it freezes, can you post the output of

/var/log/messages

?

---

### Post by magicdanw on 2009-05-28
Pretty much, I just ran an upgrade from 8.10 to 9.04, and the system seemed to have a bunch of problems.  It was making me log in twice, Firefox tended to freeze up and not quit if I, say, ran VLC at the same time, and some other problems.  However, this morning, the sluggishness seems to have disappeared! :) I'm going away for a few days without my laptop or internet, but when I get back, if the problems are still...well...problematic, I'll post back here.  Otherwise, things are looking pretty good! :)

In case I don't return to this thread, thanks a lot to both Raymond and Steel! :D

---

### Post by raymondh on 2009-05-28
and in case you don't return ... you're welcome :)

Have a good trip.

---

