---
title: "&quot;apt-get --reinstall install foo&quot; vs. &quot;apt-get purge foo&quot; + &quot;apt-get install foo&quot;"
date: 2009-07-08
forum: Installation &amp; Upgrades
---

### Post by rajanski on 2009-07-08
Hello I have a weird problem with ubuntu jeos 8.04,

I am having a selfmade package with no conffile entries and no dependencies. This package is to be installed in /opt.

1.Now when I am trying to upgrade this single package with 
apt-get --reinstall install foo, everything is working but the files are not copied into /opt, so the package is marked as installed but in fact is not really installed at all.

2.As a workaround I removed the package with apt-get purge foo and the installed int normally with apt-get install foo and it worked.

Due to already distributed virtual machines containing the apt-get --reinstall install foo line in cron, I have to find a way to make Option 1 working.

Any help is very apreciated! Greetings from Berlin!

---

