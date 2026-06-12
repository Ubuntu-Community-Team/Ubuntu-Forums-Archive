---
title: "[SOLVED] No panel appearing in firefox"
date: 2008-11-14
forum: General Help
---

### Post by thestig_992 on 2008-11-14
My firefox just started acting rly weird the other day; its not in fullscreen mode, but my gnome panel nor my window bar (with the minimize, close buttons, etc) both dont appear. Also, my auto hiding cairo dock wont appear either. I cant use alt + F8 to resize the window, or unmaximise it. 
Yesterday i fixed it, but i really dont remember how...then when i rebooted it went back again...? No idea what to do here, any help appreciated.

---

### Post by iKonaK on 2008-11-14
You could try to run metacity or things like this but the easiest would be to just make a new user and copy what settings you need from your actual account.
Alt+F2 and > ```
users-admin
```

---

### Post by olskar on 2008-11-14
Check [http://ubuntuforums.org/showthread.php?t=981900](http://ubuntuforums.org/showthread.php?t=981900) where I have the same problem (I think?)

Disabling the "legacy fullscreen support" option in compiz workarounds plugin helped for me

---

### Post by philinux on 2008-11-14
Sys>Prefs>Compiz config. Click the effects category. Try unticking then ticking window decoration.. It's bottom left on that screen.

---

### Post by Yellow Pasque on 2008-11-14
Enter about:config in the URL bar.
Toggle browser.fullscreen.autohide to false. Better?

---

### Post by thestig_992 on 2008-11-14
> **olskar said:**
> Check [http://ubuntuforums.org/showthread.php?t=981900](http://ubuntuforums.org/showthread.php?t=981900) where I have the same problem (I think?)

Disabling the "legacy fullscreen support" option in compiz workarounds plugin helped for me

Hooray, it works, ty. Ty everyone else as well...

---

