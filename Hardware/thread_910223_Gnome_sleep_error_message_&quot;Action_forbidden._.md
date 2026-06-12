---
title: "Gnome sleep error message &quot;Action forbidden. Policy timeout is not valid ...&quot;"
date: 2008-09-04
forum: Hardware
---

### Post by amn108 on 2008-09-04
Everytime my Lenovo Thinkpad T61 laptop resumes Gnome desktop from sleep, i get a

"Action forbidden. Policy timeout is not valid..."

tooltip error message in the corner of the screen with a battery icon on it. I suspect this has to do with ACPI internals, and Gnome is just reacting on some sort of a deeper error.

Still, anyone knows what EXACTLY does this mean. Which action is it that is forbidden, and what policy and what timeout that are not valid? The message makes little sense to me.

Also, is it possible to somehow trace the message source, to identify where it came from?

---

### Post by jerich007 on 2008-09-05
I have the same issue with my T61.  But it doesn't happen all the time.  Not sure what the common symptom is that triggers it.

---

### Post by amn108 on 2008-09-06
I think we ought to try bring this issue up on [www.thinkwiki.org](www.thinkwiki.org). Those guys know a good deal more about Thinkpads vs Linux.

I am guessing Gnome has nothing to do with this, it is the internals (kernel modules or something like them) that malfunctions. Gnome merely reacts on these erroneous conditions.

---

