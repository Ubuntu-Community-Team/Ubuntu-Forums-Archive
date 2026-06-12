---
title: "Add/remove synaptic and auto updates won't load, help!"
date: 2008-08-13
forum: General Help
---

### Post by scutterflux on 2008-08-13
First off, I'm not sorry _yet_ that I'm a total newbie trying to convert from Win.  It's a challenge, but I'm sure it'll be worth it.  Any help would be greatly appreciated.

I'm not sure what's gone wrong, but add/ Remove, synaptic package manager, and the auto updates will only load for a second, and then shut back down.  The auto update is giving me a caution sign in the "panel???"

I've searched and found someone else on this forum with a similar problem, but he had no responses.

Thank You

---

### Post by Ryadt on 2008-08-13
> **scutterflux said:**
> First off, I'm not sorry _yet_ that I'm a total newbie trying to convert from Win.  It's a challenge, but I'm sure it'll be worth it.  Any help would be greatly appreciated.

I'm not sure what's gone wrong, but add/ Remove, synaptic package manager, and the auto updates will only load for a second, and then shut back down.  The auto update is giving me a caution sign in the "panel???"

I've searched and found someone else on this forum with a similar problem, but he had no responses.

Thank You

Try in terminal ```
sudo apt-get update
``````
sudo apt-get upgrade
```

---

### Post by ibutho on 2008-08-13
Hi

To diagnose the problem, run Applications -> Accessories -> Terminal and enter
```
sudo synaptic
```
Post back any error messages that get printed in the terminal.

---

### Post by scutterflux on 2008-08-13
segmentation fault

---

### Post by scutterflux on 2008-08-13
I'm also running the update using terminal now, maybe that'll fix something, I'll get back to you shortly.

---

### Post by scutterflux on 2008-08-13
That update seems to have fixed it.
Thanks for the help.

---

