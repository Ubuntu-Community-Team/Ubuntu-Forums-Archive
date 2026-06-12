---
title: "Synaptic &quot;Quick Search&quot; Not Functional in Alternate CD Install of Intrepid"
date: 2008-11-07
forum: General Help
---

### Post by sstecken on 2008-11-07
Just did a full encryption install of Ibex and in Synaptic Package Manager, the "Quick Search" box does not seem to function.

If I use the "Search" button, it seems to work but no results show up.

Any ideas on how to fix?

---

### Post by dcstar on 2008-11-08
> **sstecken said:**
> Just did a full encryption install of Ibex and in Synaptic Package Manager, the "Quick Search" box does not seem to function.

If I use the "Search" button, it seems to work but no results show up.

Any ideas on how to fix?

"Quick Search" is a filter option which functions on whatever you have visible on the screen - it is not a general search function.

---

### Post by bbabu84 on 2008-12-14
> **dcstar said:**
> "Quick Search" is a filter option which functions on whatever you have visible on the screen - it is not a general search function.

I have installed xubuntu 8.10, and there is definitely a problem with the Quick search feature.  I am looking at "All" on the left bar, which shows all packages on the screen.  If I type a string in the Quick search box, it filters it and shows only the packages that have been installed.  None of the new (uninstalled) packages show up.  For example, 3dchess is right there on top, and as soon as I enter "3d" or "chess", it is no longer on screen.  Instead I get all *installed* packages that have "3d" in them or "chess" in them.  On another system, I have installed ubuntu 8.10 (not xubuntu) and in that system, Quick search seems to function fine.  Any help in fixing this problem is appreciated.

BB

---

### Post by kuehlakku on 2009-02-04
Hi,

I had the same issue with xubuntu 8.10. Just enter 'sudo update-apt-xapian-index' in a terminal. After this the quick search will take all packages into account.

---

### Post by aaron@roydhouse.com on 2009-04-04
Using Ubuntu 8.10 I've found some keywords or packages that quick-search just won't match, 'cinelerra' is one. The regular search finds matches for a 'Name' search no problem. Running this update you mention below didn't fix it.

This drives me crazy, because it keeps mis-leading me as to what is and isn't in repositories.

> **kuehlakku said:**
> Hi,

I had the same issue with xubuntu 8.10. Just enter 'sudo update-apt-xapian-index' in a terminal. After this the quick search will take all packages into account.

---

