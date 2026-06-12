---
title: "New Install of Ubuntu 9.10, Gimp Does Not Launch"
date: 2009-11-11
forum: Installation &amp; Upgrades
---

### Post by WilliamCampbellJr on 2009-11-11
So far I'm very happy with Ubuntu 9.10, but I can't seem to get Gimp (which came pre-loaded with the install) to launch, and I don't know where to begin looking for the cause. I tried to uninstall and download another version, but I noticed in the terminal that the old version, which I had thought I had trashed, was located and reinstalled. Don't know if that makes a difference. At any rate, when I click on the launcher icon, the little spinning disk appears for about fifteen seconds, then disappears. The Gimp opening window never does materialize.

I appreciate any input on where to begin looking for the solution to this problem. It doesn't appear that many other users are having this issue!

Thanks again.

Bill Campbell

---

### Post by WilliamCampbellJr on 2009-11-11
Well. Seems as if the new install of 9.10 neglected to include the libgegl -0.0-0 file. 
[INDENT]gimp-2.7: error while loading shared libraries: libgegl-0.1.so.0: cannot open shared object file: No such file or directory[/INDENT]Located it, downloaded and installed it, and presto, the Gimp is up and about!

Cheers!

---

