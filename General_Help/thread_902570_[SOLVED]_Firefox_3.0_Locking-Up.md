---
title: "[SOLVED] Firefox 3.0 Locking-Up"
date: 2008-08-27
forum: General Help
---

### Post by WolfWitch on 2008-08-27
I can't find anything current about this, so figured I would start here...

For the record- I've been using Ubuntu as my primary desktop OS both at home and work for over two years.

Recently (as in the last week), Firefox 3.0 started routinely locking up. It seems to happen if more than 2 windows or tabs are open, and it does not appear to be related to the "usual" npviewer problems. (Running 64-bit.) It will just suddenly go dim and completely lock (all windows). It happens on two different systems, a home desktop and work laptop, both 64-bit.

I routinely run "killall npviewer.bin" when Firefox locks-up, since until this started happening- that was the problem 100% of the time. Unfortunately that no longer seems to be the case. The only option is to force-quit Firefox. I've given it as long as an hour to recover by itself, and it just doesn't happen.

Also- I am not showing high CPU or memory/pagefile usage when this happens- Firefox simply locks.

So- any help or a point in the right direction would be greatly appreciated. I can't really find anything online mentioning this problem, and I'm very curious if anyone else is experiencing it. Most of my friends with Ubuntu are running 32-bit versions, and haven't been having the same issues.

---

### Post by WolfWitch on 2008-08-27
I should have looked at the obvious similarities between the two machines first- Firefox Plug-Ins. It appears that current versions of the Google Toolbar and the Del.icio.us Plugin are causing this behavior. If I install one or both of them- I can quickly get Firefox to lock up. With them disabled or uninstalled- it works like a charm, with dozens of windows or tabs open at once.

Not sure what these two plug-ins have in common, other than requiring their own Internet access to function, but I can live without both. :)

---

