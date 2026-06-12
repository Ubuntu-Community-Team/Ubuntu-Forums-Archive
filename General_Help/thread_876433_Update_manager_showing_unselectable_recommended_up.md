---
title: "Update manager showing unselectable recommended update"
date: 2008-07-31
forum: General Help
---

### Post by Martym on 2008-07-31
For a while now, not sure how long, update manager always said there was one more update available then what was listed.  I looked around for an answer to that but I was not too concerned about it.  Today there were lots of updates available and I applied all of them.  Now the count is correct and I have one update left for gnome-panel but I am unable to select it.  It sits on the window, box unchecked, mocking me right under the Recommended updates header.

Is there a way I can select or remove it?

---

### Post by Diabolis on 2008-07-31
Try to do it in a terminal:

```
sudo apt-get update
sudo apt-get upgrade
```

---

### Post by Martym on 2008-07-31
Looks like that will work but it will also update all the items I locked in Synaptic.  Guess I will work on removing those first.

---

### Post by Diabolis on 2008-07-31
No, it shouldn't update locked packages. Synaptic is just a graphic client, in its guts it uses dpkg, apt-get uses dpkg too.

dpkg is the only way to install/uninstall packages in ubuntu.

---

