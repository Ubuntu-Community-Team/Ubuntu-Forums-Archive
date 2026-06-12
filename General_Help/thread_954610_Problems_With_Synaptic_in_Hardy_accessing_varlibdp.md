---
title: "Problems With Synaptic in Hardy accessing /var/lib/dpkg/status"
date: 2008-10-21
forum: General Help
---

### Post by albedo on 2008-10-21
When using Synaptic in Hardy, I encounter the following problem :

When I search for a package using the "search" function, and then try to do something with that package, i.e. "install", any attempt to apply my changes produces the following error:

E: Unable to parse package file /var/lib/dpkg/status (2)
E: Unable to lock the download directory

This error does not appear if I manually browse to the package - e.g. through "sections" - and then select and apply my changes. It also doesn't happen if I install the package through other means, e.g. apt-get or dpkg -i.

After some searching around through Google, I found the following work-around :

Instead of clicking "Apply", first try "Fix broken packages" from the drop-down menus twice. First, it will generate mentioned error. The second time, it won't. At that point, I can effectively apply my changes...

I can't find anything about it in bug reports for Synaptic though, and any further references online seem obscure at best.

It's the weirdest thing... I've been using Gutsy for about a whole year and never had a problem using Synaptic - always worked like a charm. Until I installed Hardy fresh onto my new box.

Anyone have an idea of what might be up?

---

