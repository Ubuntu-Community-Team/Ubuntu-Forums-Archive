---
title: "Synaptic authentication problem"
date: 2008-12-21
forum: Installation &amp; Upgrades
---

### Post by dougalkerr on 2008-12-21
I have been trying to update through synaptic and can't complete the reload of updates because I am running into an authentication problem as one of the lines shows;

"Failed to fetch [http://archive.canonical.com/ubuntu/...86/Packages.gz](http://archive.canonical.com/ubuntu/...86/Packages.gz) 407 Proxy Authentication Required"

and another

"Failed to fetch [http://mirror.ox.ac.uk/sites/archive...86/Packages.gz](http://mirror.ox.ac.uk/sites/archive...86/Packages.gz) 407 Proxy Authentication Required
Some index files failed to download, they have been ignored, or old ones used instead."

I have made sure my browser is not working through a proxy (but have tried it through one as well with no difference).
What do I need to do to solve this?? Thanks...

---

### Post by Partyboi2 on 2008-12-21
If you are using a proxy then check that your settings are correct in Synaptic Package Manager (System>Admin>Synaptic>Settings>Pref>Network) If you don't use a proxy then make sure that "direct connection to internet" box is marked.

---

### Post by dougalkerr on 2008-12-26
Thanks I will look at this. I have the problem on another machine right now but, have looked at the settings on this old laptop which is working and it is 'Direct Internet Connection'.
Thanks again.

---

