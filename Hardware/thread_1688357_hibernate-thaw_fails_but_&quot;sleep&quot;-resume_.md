---
title: "hibernate-thaw fails but &quot;sleep&quot;-resume works"
date: 2011-02-15
forum: Hardware
---

### Post by SaintDanBert on 2011-02-15
My laptop will suspend-to-ram (sleep) and resume-from-suspend (resume) without any troubles.

I cannot get that same laptop to suspend-to-disk (hibernate) and resume-from-hibernate (thaw). Also, I cannot discover any way to diagnose and troubleshoot this failure. 

What makes this a royale pain is the fact that I have a second identical laptop the works just fine. I'm dashed if I can find any differences that have any bearing on what is happening.  (BTW -- Canonical support can't find it either.)

Can anyone help me shed light on what is going on?
~~~ 0;-/

===== ===== ===== ===== ===== ===== ===== ===== ===== =====
Follow-up:
   When reading the power-management details, they use these words
with the following meaning:
**suspend** -- suspend-to-ram; what some call "sleep"
*System state gets saved and everything powers down to minimums but does not turn power off.*
**resume** -- restart after "sleep"
*restart does not involve a trip through grub*
**hibernate** -- suspend-to-disk
*System state gets saved follow-ed by power-off shutdown*
**thaw** -- restart after "hibernate"
*restart involves power-on (reset) and a trip through grub*.

Sadly, they also use the term "resume" for any restart after either of
"sleep" and "hibernate" so read carefully.
===== ===== ===== ===== ===== ===== ===== ===== ===== =====

---

