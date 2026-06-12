---
title: "Can I reuse downloaded packages"
date: 2008-11-07
forum: General Help
---

### Post by Offramp on 2008-11-07
Hi all,

I currently have both ubuntu and kubuntu installed on different partitions on a single hard drive.  I am still trying to work out which is the best environment for me and consequently I am installing different kde and gnome applications.

Is it possible to have Synaptic and Adept use packages that have already been downloaded.  For example, I have just installed eclipse in my KDE environment, to save downloading another ~70 MB can I use these packages again in Synaptic.  

I know I can install both gnome and kde in the one partition, but I would like to chose one and stick with it.

Cheers

---

### Post by Idefix82 on 2008-11-07
> **Offramp said:**
> Hi all,

Is it possible to have Synaptic and Adept use packages that have already been downloaded.  For example, I have just installed eclipse in my KDE environment, to save downloading another ~70 MB can I use these packages again in Synaptic.  

Cheers

Yes, it is. You can just copy the downloaded files into the /var/cache/apt/archives directory of the partition where you want to install it and open Synaptic there. I think if you tell it to install the package, Synaptic will automatically first check whether it has already got it in its cache.

---

