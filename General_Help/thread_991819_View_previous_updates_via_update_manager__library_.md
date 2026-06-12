---
title: "View previous updates via update manager?  library update broke my RPC code"
date: 2008-11-24
forum: General Help
---

### Post by gogetadbl on 2008-11-24
I ran some updates from the update manager but I don't remember the exact libraries that were updated.  After the update, I was getting runtime errors for my RPC code. Is it possible to get previous versions of the libraries I had before or is there a system restore type feature to go back to yesterday? 

On client side I am getting Error is localhost: RPC: Unable to receive; errno = Connection reset by peer.

On server side I am getting segmentation faults (core dumped).

---

### Post by zvacet on 2008-11-24
**Synaptic>file>history** to see what did you upgrade.After that look in var/cache/apt/archives and see if you have previous versions of libraries.If you do delete one you downloaded with apdate manager and install old ones.After that go to the synaptic and find that packages and go to the file tab and select **lock version**.That way packages will not be upgraded.

---

