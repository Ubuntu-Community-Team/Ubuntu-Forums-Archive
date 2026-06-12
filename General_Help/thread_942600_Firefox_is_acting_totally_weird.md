---
title: "Firefox is acting totally weird"
date: 2008-10-09
forum: General Help
---

### Post by TheBootstrapKid on 2008-10-09
i'm a novice user of ubuntu.  here's whats going on.  firefox is extended to the borders of my screen.  the system bar at the top is not visible and neither is the bar at the bottom.  additionally firefox keeps flashing a black screen.  what's the deal?

---

### Post by jerome1232 on 2008-10-09
Did you accidently fullscreen it? (f11) or perhaps your borders just aren't loading form some reason, try reloading compiz or metacity to get the bars back.

---

### Post by Ameya Koshti on 2008-10-09
m facing the same prob with firefox 3 b5.....
but with firefox 2 it doenst happen....
y the final release of firefox3 is not out for ubuntu????

---

### Post by bcom on 2008-10-09
I had a similar problem after firefox updated.  Here is how I fixed it.

In the address bar, type about:config

Scroll down to find the preference name browser.fullscreen.autohide

Change the value from false to true and restart Firefox

---

### Post by mbeach on 2008-10-09
I've found that the flickering can be stopped with the following when in fullscreen mode:
[http://tombuntu.com/index.php/2008/09/03/fix-for-flickering-fullscreen-application-with-compiz/](http://tombuntu.com/index.php/2008/09/03/fix-for-flickering-fullscreen-application-with-compiz/)

excerpt:
```
gconftool-2 --set /apps/compiz/general/screen0/options/unredirect_fullscreen_windows --type bool 0
```

---

