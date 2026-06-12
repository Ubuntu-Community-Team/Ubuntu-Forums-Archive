---
title: "Why does sudo run-parts -v /etc/cron.daily take forever in Hardy?"
date: 2008-07-17
forum: General Help
---

### Post by gobbles414 on 2008-07-17
I know that I'm being a bit paranoid. But occasionally, I like to manually run my crons. For example, *sudo run-parts -v /etc/cron.daily*. I am using Ubuntu Hardy 64-bit. I've marked this thread *all variants*, since I suspect this problem exists in many Hardy-based operating systems.

In Gutsy, all crons run acceptably fast. I would estimate that running daily, weekly, and monthly takes a grand total of two minutes. But in Hardy, the apt portion of daily takes fifteen minutes! Scrollkeeper in monthly also takes a long time to complete, compared to the same cron in Gutsy. These problems exist in both 32-bit Hardy and 64-bit Hardy, on at least two different PCs.

Before I submit a bug report on this issue, I want to make sure that I'm not making a silly mistake in my command line syntax, etc. **Any ideas?** Thanks in advance.

---

### Post by gobbles414 on 2008-07-19
Bump

---

### Post by gobbles414 on 2008-07-26
Bump 2.0

---

### Post by gobbles414 on 2008-07-29
Bump 3.0

---

### Post by gobbles414 on 2008-08-04
For the past few days, the *apt* portion of *daily* has been running much faster in 32-bit Hardy than before! *Scrollkeeper* in *monthly* has also be completing more quickly in 32-bit Hardy than previously. I assume that some recently-released update is responsible for the improved speed...? I haven't had a chance to re-test 64-bit Hardy.

Running *daily*, *weekly*, and *monthly* sequentially in Hardy used to take anywhere from 20 minutes to over half-an-hour. To finish all of these crons now takes a grand total of about 10 minutes. Although this improved time is still not as fast as the same crons would be in Gutsy, I can live with 10 minutes. So I'll mark this thread as solved.

---

### Post by gobbles414 on 2008-08-29
Well, I apparently marked this thread as SOLVED to quickly. These crons are now running slower than ever. I'm going to re-mark the thread as unsolved.

---

