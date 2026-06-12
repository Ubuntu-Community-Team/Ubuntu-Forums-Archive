---
title: "Apache Help"
date: 2008-08-09
forum: General Help
---

### Post by mikeylikesit on 2008-08-09
Hey Guys, while messing with my server i have managed to delete my /etc/apache2/ports.conf and and apache2.conf. I reinstalled apache and it did not seem to fix it. Can someone please tell me to how to completely reinstall every thing with Apache. Any Help would be great. 

Thanks in advance!!

---

### Post by RealPSL on 2008-08-10
Before you do this please make sure you backup any configuration files from apache that you want to keep. It would also be easier to help if you could provide details on what is not working as maybe it can be fixed.


To completely remove apache and any of the configuration files you would run:
```
sudo apt-get purge apache2
```

To remove any unneeded packages that may be left behind you would run
```
sudo apt-get autoremove
```

To reinstall apache you would eun
```
sudo apt-get install apache2
```

---

