---
title: "Compiz screwed up my computer BADLY, now it is innacessable!"
date: 2008-11-24
forum: General Help
---

### Post by FSXmann on 2008-11-24
OK I was screwing around with the CompizConfig Settings Manager and I enabled a plugin called "Mouse position polling" or something like that, then my screen went black and it showed the login screen. When I tried to log back in, same thing: I got rerouted back to the login screen. I logged into a failsafe terminal session and uninstalled compizconfig-settings-manager, but I still can't log in. HELP!!!!

P.S. I'm on a laptop and the video card really sucks. Maybe that is the problem?

---

### Post by astoltz on 2008-11-24
You can undo ALL your compiz settings with the following command:```
gconftool --recursive-unset /apps/compiz
```

Be aware that this will undo ALL of your custom settings.

---

### Post by Jackelope on 2008-11-24
Or.... 

```
metacity --replace
```

in a terminal. I screwed up my compiz config and couldn't log in either. I booted into terminal-only mode and typed it, even though I couldn't see what I was typing. Worked great.

---

