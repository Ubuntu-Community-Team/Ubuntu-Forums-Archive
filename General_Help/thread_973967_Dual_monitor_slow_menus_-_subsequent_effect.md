---
title: "Dual monitor slow menus - subsequent effect"
date: 2008-11-07
forum: General Help
---

### Post by FinnNormannPedersen on 2008-11-07
I set up desktop to support dual monitors (LCD+Projector) and it works fine, except for the slow menu problem described and solved in this thread:

[http://ubuntuforums.org/showthread.php?t=536045&highlight=compiz+slow+menus&page=5](http://ubuntuforums.org/showthread.php?t=536045&highlight=compiz+slow+menus&page=5)

Solution is basically add a script during boot:
```

DISPLAY=:0.0 compiz --only-current-screen &
DISPLAY=:0.1 compiz --only-current-screen &

```

However I get a subsequent problem that I can no longer control how my desktop work. Cannot setup virtual desktops or use 3d cube desktop.

Any ideas?

---

