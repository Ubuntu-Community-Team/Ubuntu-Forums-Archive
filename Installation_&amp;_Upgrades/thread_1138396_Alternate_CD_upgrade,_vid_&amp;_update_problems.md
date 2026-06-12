---
title: "Alternate CD upgrade, vid &amp; update problems"
date: 2009-04-26
forum: Installation &amp; Upgrades
---

### Post by Northsider on 2009-04-26
I upgraded with the alternate install CD.  Rebooted and ran the update manager.  I now have this message:
[IMG]http://i42.tinypic.com/2rel8qb.png[/IMG]

When I run the 'partial upgrade' it download the packages, but then crashes out and doesn't install them
[IMG]http://i42.tinypic.com/i6axj9.png[/IMG]

Crashes out right after this last package
[IMG]http://i39.tinypic.com/2yk1jj9.png[/IMG]

Also, I went to play URban Terror after the upgrade and it's choppy and the sound is messed up.  Any ideas?

---

### Post by Triptol on 2009-04-26
You could try the following from a terminal:
```
sudo aptitude dist-upgrade
```

It might deinstall some programs you rely on, so please take note and reinstall them afterwards.

---

### Post by Northsider on 2009-04-26
Thanks...I think it worked.  I also had to re-enable my restricted drivers.

---

### Post by Triptol on 2009-04-27
Glad that helped.

---

