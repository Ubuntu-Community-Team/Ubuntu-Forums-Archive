---
title: "[SOLVED] Firefox &amp;quot;Illegal instruction&amp;quot; issue."
date: 2008-09-25
forum: General Help
---

### Post by Senesence on 2008-09-25
I found threads that talk about potential causes of the problem; this one in particular: [http://ubuntuforums.org/showthread.php?t=800086](http://ubuntuforums.org/showthread.php?t=800086)

My strace output is basically the same, and I also did not have the libxul-common and libxul0d libraries installed.

So, I installed those, and hoped that it would do the trick just like for the guy in that thread...but it didn't, and now I can't start firefox; all I get is "Illegal instruction".

....Help!

---

### Post by Sef on 2008-09-25
What version of ubuntu are you using?

---

### Post by Senesence on 2008-09-25
> **Sef said:**
> What version of ubuntu are you using?

Ubuntu 8.04 (Hardy)

---

### Post by Senesence on 2008-09-27
Ok, there was a new update, and the issue was fixed.

I got by on using the standalone version of firefox, which I downloaded directly from their webpage, and that worked fine until the update got through.

---

