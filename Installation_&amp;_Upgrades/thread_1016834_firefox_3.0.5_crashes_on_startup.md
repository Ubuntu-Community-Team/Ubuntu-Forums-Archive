---
title: "firefox 3.0.5 crashes on startup"
date: 2008-12-20
forum: Installation &amp; Upgrades
---

### Post by transkinetic on 2008-12-20
Hello,
I'm using Xubuntu 8.1. Firefox had been working error free until I updated it to 3.0.5 via the update manager. Now whenever I try and run firefox, it just hangs. I can see firefox in System Manager's process viewer.

I'm using elinks right now. It's fairly spiffy but I can't see images or the youtube.

Can I somehow revert to the previous version of firefox?
Also, is there some sort of text/terminal browser that will embed images?

---

### Post by taurus on 2008-12-20
Can you run firefox from a terminal to see what's wrong with it?

```
firefox
```

---

### Post by transkinetic on 2008-12-20
No information is returned. The Process hangs until it is ended or killed.

---

### Post by Ender41 on 2008-12-20
> **transkinetic said:**
> No information is returned. The Process hangs until it is ended or killed.

 Try opening a terminal cd to .mozilla/firefox in your home directory.
Then ls to see the name of your firefox folder, cd into that and then ls -a and rm the lock and .parentlock files. Then cd ~ and try firefox again, if it starts up then make sure you clear the cache.

Ender

---

### Post by transkinetic on 2008-12-20
There was no 'lock' file. I rm'd '.parentlock' in a subdirectory named pr98li3b. Starting firefox recreated '.parentlock' . Still no change. Firfox is but an entry in the process list and there's no terminal output.

I tried removing all the cache files and deleting most of the config files with no effect at all.

---

### Post by Ender41 on 2008-12-21
> **transkinetic said:**
> There was no 'lock' file. I rm'd '.parentlock' in a subdirectory named pr98li3b. Starting firefox recreated '.parentlock' . Still no change. Firfox is but an entry in the process list and there's no terminal output.

I tried removing all the cache files and deleting most of the config files with no effect at all.

Ok make sure firefox isn't running and create a new profile
using ./firefox -profilemanager 
from a terminal. If it still crashes then you may need to try deleting the whole .mozilla folder, though this will lose bookmarks etc and is not the best solution.

Ender

---

### Post by transkinetic on 2008-12-21
Thanks for the replies. I ended up installing the latest firefox beta. It works. Yay. :KS

---

