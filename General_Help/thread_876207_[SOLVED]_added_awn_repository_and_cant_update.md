---
title: "[SOLVED] added awn repository and cant update"
date: 2008-07-31
forum: General Help
---

### Post by flytripper on 2008-07-31
Hi I added the awn repository to my list, updated and now there are updates showing in the update manager under "other updates" but i cant tick the box to allow them to be updated when i click update. am i missing something?

---

### Post by Diabolis on 2008-07-31
This is what I added to my sources.list file:
```
deb http://ppa.launchpad.net/awn-testing/ubuntu hardy main
deb-src http://ppa.launchpad.net/awn-testing/ubuntu hardy main

```

And it works.

```

sudo apt-get update
sudo apt-get install avant-window-navigator
```

---

### Post by flytripper on 2008-07-31
thanks . i already have it installed. its just showina an available update in update manager and i cant install it (greyed out) for some reason

---

### Post by Diabolis on 2008-07-31
Does an available upgrade shows up if you run **sudo apt-get upgrade**?

---

### Post by flytripper on 2008-07-31
yea thanks

---

