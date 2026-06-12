---
title: "perl problem between two machines"
date: 2008-09-16
forum: General Help
---

### Post by edrimon on 2008-09-16
Hi 

at first sorry for my poor grammar.
i am using the same perl script in 2 servers.

The first machine perl -v says: This is perl, v5.8.8 built for x86_64-linux-gnu-thread-multi

the second: This is perl, v5.8.8 built for i486-linux-gnu-thread-multi

In the second machine the script runs normally, in the first one says: Can't locate object method "new" via package "ArticleParser" at MarketWatch/ArticleParser.pm line 10.

Isnt it weird? 

I need help because this script runs on cron every day and collects data for the needs of our lab ([www.intelligence.tuc.gr](www.intelligence.tuc.gr))

The code ran normally in the previous machine, seems to have no mistakes. We upgraded to a x86_64 server and stopped working, showing the error above.

Thanks!

---

### Post by ghostdog74 on 2008-09-16
make sure you install extra 3rd party packages in both machines.

---

