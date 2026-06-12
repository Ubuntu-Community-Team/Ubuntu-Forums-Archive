---
title: "Remove noexec option from automount"
date: 2005-11-14
forum: General Help
---

### Post by JedTheHead on 2005-11-14
When removeable media (i.e. a USB drive) is inserted, it is automatically mounted.  This is good.

When mounted, it is given the "noexec" option, as well as others.  This is good for security, but not what I want.

If added to the fstab I can get rid of the noexec flag, but it will no longer be auto-mounted.  This is good / bad.

I assume all this is handled in the hal, but cannot find where to change the default options.  autofs doesn't appear to be being used (unless I am an idiot and can't find it) as I have no auto.master, etc. in /etc.  

Anyone know where I can go to change the automount behavior?

Thanks!

Jed

---

### Post by Scunizi on 2006-03-22
I saw your question while looking for answers for my own.  In your case you might go to System/Preferances/Removable Drives & Media and uncheck the automount option.  By this time though, you've either given up on an answer, found it in another location or gone back to w*.  I hope this helps.

---

