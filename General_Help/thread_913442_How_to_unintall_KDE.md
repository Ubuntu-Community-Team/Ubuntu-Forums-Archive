---
title: "How to unintall KDE"
date: 2008-09-07
forum: General Help
---

### Post by theedudenator on 2008-09-07
I am running the current version of ubuntu.
I tried the KDE system, but it crashed and not all the hardware worked correct.

So now I want to go back to gnome and remove KDE.

I did the add/remove of KDE, but my boot screen and login are still kubuntu.

---

### Post by kjohansen on 2008-09-07
This will remove all the KDE specfic applications:
[http://www.psychocats.net/ubuntu/puregnome](http://www.psychocats.net/ubuntu/puregnome)

Get spalsh screens back:
[http://ubuntuguide.org/wiki/Ubuntu:Gutsy#How_to_change_the_USplash_Screen_on_startup.2Fshutdown](http://ubuntuguide.org/wiki/Ubuntu:Gutsy#How_to_change_the_USplash_Screen_on_startup.2Fshutdown)

I did this not too long ago and I believe there was a bug that required a work around...

Edit: this might have been the workaround:
```

sudo dpkg-reconfigure linux-image-`uname -r`

```

---

