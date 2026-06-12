---
title: "Pidgin: problem with launch after update from 3.5.8 to 2.6.1"
date: 2009-08-26
forum: Installation &amp; Upgrades
---

### Post by RomanIvanov on 2009-08-26
Xubuntu 9.04 (after update from 8.10).

After update from Launchpad repository, I get following error

pidgin: symbol lookup error: pidgin: undefined symbol: purple_theme_loader_get_type

Does anybody solved that problem ?

---

### Post by Partyboi2 on 2009-08-27
Hi, try 
```
sudo ldconfig
``` as mentioned [URL="http://sangprabo.blogspot.com/2009/08/how-to-install-pidgin-from-source-in.html"][COLOR=Blue]here.[/COLOR]
[/URL]

---

### Post by RomanIvanov on 2009-08-27
thanks for reply, I tried it - does not help.

I tried even reinstall completely pidgin - did not helped.

Any ideas ?

---

### Post by Ronnie76er on 2009-08-31
I am having the same problem.  I upgraded pidgin from the PPA repo and it was working fine.  Just today, I did a sudo apt-get upgrade.  After I did that, pidgin no longer worked correctly.  

I tried going with 2.5.5, but I think the new version did something to my configuration files, so I can't see my buddy list when I start it up.

sudo ldconfig does not fix it.

---

### Post by Ronnie76er on 2009-09-01
I was able to fix it by building 2.6.1 from source.  You can look at that link above to show you how.

One good idea is to keep around that build, so that if you do decide to go with the one from the repos again, you can just do a 'sudo make uninstall' from the source directory to uninstall it.

---

