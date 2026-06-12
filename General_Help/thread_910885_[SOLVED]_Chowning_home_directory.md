---
title: "[SOLVED] Chowning home directory"
date: 2008-09-05
forum: General Help
---

### Post by jasex on 2008-09-05
Ok... i've recently had issues... for those of you whom have already read about me deleting my /bin... re-installed... tried rescuing /etc, that ended up in me having to re-install again... so I scrapped that...

Lately I've noticed most of my user configured things are fluxxed up when it comes to important things like my logitech keyboard not registering under keyboard shortcuts anymore using its XF86 key sign, and ends up using the base keysign like 0x*** so I can't use any of my media keys with amarok anymore... which is crappy since I had JUST recently gotten them to work... and other severe things are wrong...

ok down to the nitty gritty...

would performing

```
sudo chown -R xase:xase /home/thursday
```

and plucking what i specifically need like pictures music, virtualbox stuff be a bad idea...??? all stuff would obviously be moved to /home/xase

 and what files should I save other than that, that more than likely have no affect on what could be wrong and might want to save like themes and such?

---

### Post by jasex on 2008-09-05
Un-Fixed

CTRL-ALT-DEL and Logout button don't bring up menu, instead freeze xsession almost entirely except cursor still moves... I somehow just recently fixed this on my other login... but now it's happening to this login.

---

### Post by jasex on 2008-09-06
OP fix concluded, thanks for the help.

Deemed relatively safe, granted you pay attention, and textually modify some files.

---

