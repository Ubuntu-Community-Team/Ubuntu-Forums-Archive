---
title: "HELP! gamin (gam_server) problem"
date: 2005-11-30
forum: General Help
---

### Post by ERam123 on 2005-11-30
Hi all.

I just recently moved over from Gentoo... got tired of everthing taking 50x longer than I really wanted to invest as far as configuring and installing and compiling software.  (FWIW It was fun while it lasted, and I learned about linux in the process).

Anyhow, enough with the autobiography.  I am having the dreaded gamin problem.  (100% cpu usage, bringing my system to a halt, hard reset required!)  I have read all about possible solutions, but each time the author later comes back and says it didn't actually fix the problem.

I was wondering if there has been any progress on this lately.  Also, I was wondering if i can just install gamin from the Dapper repository and see if it fixes the issue?

One last thing.  The Breezy Badger gamin seems to be 0.1.5 and Dapper seems to be 0.1.7-r2 or something similar.  Where is the 0.1.6?  I read somewhere this might have been a problem fixing release?

ANY help would be AWESOME at this point.

If its any help helping me, all my drives are reiserfs (3.6.... the stable one) and I have AMD Athlon 1500+ and 512mb RAM.

---

### Post by Shashmik on 2005-12-01
Hey, i have this problem as well - real pain in the arse. It allways occurs when i try to access an NTFS volume on my machine.

Anyway it can be killed using ```
killall -l9 gam_server
```

Shash

---

### Post by ERam123 on 2005-12-05
such a messy solution though... is there anything else in the works?

---

