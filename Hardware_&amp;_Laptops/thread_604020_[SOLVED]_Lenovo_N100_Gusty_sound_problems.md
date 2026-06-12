---
title: "[SOLVED] Lenovo N100 Gusty sound problems"
date: 2007-11-05
forum: Hardware &amp; Laptops
---

### Post by koolguynet on 2007-11-05
I recently installed Gusty on my Lenovo 3000 N100 notebook.  Most everything works great.  Sound worked until I ran an update, then it broke.  I found a post that explained how to re-compile ALSA so I did that and sound worked again.  Then this morning sound stopped working again...so logic would have to follow the same recompile instructions, so I did and it didn't work this time.  I have tried just about every previous suggestion.  Any ideas?

From lspci:
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)

---

### Post by henklaak on 2007-11-06
Might be something trivial:

[https://help.ubuntu.com/community/DebuggingSoundProblems]("https://help.ubuntu.com/community/DebuggingSoundProblems")

Hope this works for you. Otherwise, please post some details as explained in the link. 

Greetings, Henk.

---

### Post by koolguynet on 2007-11-06
Thank you so much.  It turned out to be something in Kmix.  I feel stupid, but thanks for the link, it was a great help!

---

### Post by henklaak on 2007-11-06
Glad you solved it. Please mark the thread as solved, thankx.

---

