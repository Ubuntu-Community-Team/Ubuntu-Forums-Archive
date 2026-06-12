---
title: "help me with this error....anyone???"
date: 2009-04-20
forum: Installation &amp; Upgrades
---

### Post by emix101 on 2009-04-20
hi everybody!
I'm new to linux.currently I'm using ubuntu jaunty beta release..before this everything ok...but today when i try to update my distribution it came out some error like this:-

E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem.
E: _cache->open() failed, please report.

I already ready try to do manually by running those sudo command,
but I stuck with it because I do not know what to do next...any help??...

Thanks for ur help....

---

### Post by ad_267 on 2009-04-20
What output did you get when you ran "sudo dpkg --configure -a"?
If that worked you should be able to update again and everything should be fine. Try running "sudo apt-get update && sudo apt-get dist-upgrade"

---

### Post by emix101 on 2009-04-20
Hi thanks!
it worked...why the last time I run those command it doesn't work...
typo error???...

anyway thanks ad_267

---

### Post by ad_267 on 2009-04-20
> **emix101 said:**
> Hi thanks!
it worked...why the last time I run those command it doesn't work...
typo error???...

anyway thanks ad_267

Did it return an error last time? It might be that you thought it didn't work but it actually did. Usually when the command runs successfully it doesn't print any output so it doesn't seem like anything has actually happened. If there was an error then it's hard to say what went wrong without seeing the actual error. Glad it's working now :D

---

