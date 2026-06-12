---
title: "Compiz not loading on startup"
date: 2008-07-15
forum: General Help
---

### Post by nanbread on 2008-07-15
There is this really annoying problem that I have with my ubuntu installation, for some reason compiz doesn't load when gnome starts up. In the fusion icon it says my current window manager is compiz but it is actually metacity. Also doing a simple reload window manager solves this.

Does anyone how I can just have compiz load correctly on startup?

---

### Post by Execute_Method on 2008-07-15
Here you go.. I posted this in regards to starting compiz automatically. As well this also takes care of auto loading emerald instead of metacity.

[http://ubuntuforums.org/showpost.php?p=5386981&postcount=9](http://ubuntuforums.org/showpost.php?p=5386981&postcount=9)

BTW I use the indirect option because of my video driver. You may not have to use that option.

eg.
```
compiz --replace ccp &

```

---

### Post by tuxxy on 2008-07-15
Use sessions with 
```

compiz --replace 

```
[http://ubuntuforums.org/showthread.php?t=860357](http://ubuntuforums.org/showthread.php?t=860357)

---

### Post by nanbread on 2008-07-16
I tried both of those and it didn't work for me. However, reinstalling fusion-icon, fixed it for me. Strange. :/

---

