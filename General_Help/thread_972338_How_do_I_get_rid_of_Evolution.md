---
title: "How do I get rid of Evolution?"
date: 2008-11-05
forum: General Help
---

### Post by uid313 on 2008-11-05
How do I get rid of this Evolution?
It pisses me off! :mad:

It runs in the background all the friggin time and eats my CPU and RAM. Makes the computer take longer time to boot, and eats resources. I never ever use it!

I cant remove it. It pisses me off, I want this out of my computer! :mad:

When I try to remove it, it tries to remove ubuntu-desktop, gnome-panel, ekiga, and everything! :mad:

---

### Post by SoCalChris on 2008-11-05
"sudo apt-get remove evolution" doesn't work?

---

### Post by philinux on 2008-11-05
Or remove it via synaptic. Previously it was tied to ubuntu-desktop but no more thank goodness.

---

### Post by uid313 on 2008-11-05
evolution
evolution-common
evolution-data-server
evolution-data-server-common
evolution-webcal

Even with the package 'evolution' uninstalled, there are still processes of evolution constantly running.

anonymous 10916  0.0  0.1  28472  6388 ?        Sl   Nov05   0:00 /usr/lib/evolution/evolution-data-server-2.24 --oaf-activate-iid=OAFIID:GNOME_Evolution_DataServer_BookFactory:1.2 --oaf-ior-fd=26

---

### Post by brandon88tube on 2008-11-05
Hey if you find a solution I would like to know as well. I never use it and it just takes up space.

---

### Post by rbmorse on 2008-11-05
terminal, then sudo apt-get purge evolution

---

### Post by brandon88tube on 2008-11-05
> **rbmorse said:**
> terminal, then sudo apt-get purge evolution

Will that erase all instances of evolution and will this screw up gnome?

---

### Post by stinger30au on 2008-11-06
evolution is a magic bit of gear

the thing that sold me on it was the single button backup and restore that actually works



its light years ahead of other email s/w

---

### Post by uid313 on 2008-11-06
> **SoCalChris said:**
> "sudo apt-get remove evolution" doesn't work?
No, it does not work!
Then it wants to uninstall ubuntu-desktop, gnome-panel, ekiga and everything!

> **philinux said:**
> Or remove it via synaptic. Previously it was tied to ubuntu-desktop but no more thank goodness.
No, maybe then I can only uninstall 'evolution'.
I cant uninstall Evolution completely, becaus it just wants uninstall everything else.
I can't uninstall evolution-data-server and evolution-data-server-common.

> **rbmorse said:**
> terminal, then sudo apt-get purge evolution
Then it removes ubuntu-desktop, gnome-panel and everything.

> **brandon88tube said:**
> Will that erase all instances of evolution and will this screw up gnome?
Yes, it will!

> **stinger30au said:**
> evolution is a magic bit of gear

the thing that sold me on it was the single button backup and restore that actually works



its light years ahead of other email s/w
Oh well, thats great!
But I don't use it, and I don't want it! I want it off my computer!
I WANT IT OUT!

---

### Post by josephellengar on 2008-11-06
> **uid313 said:**
> How do I get rid of this Evolution?
It pisses me off! :mad:

It runs in the background all the friggin time and eats my CPU and RAM. Makes the computer take longer time to boot, and eats resources. I never ever use it!

I cant remove it. It pisses me off, I want this out of my computer! :mad:

When I try to remove it, it tries to remove ubuntu-desktop, gnome-panel, ekiga, and everything! :mad:

What release are you on?  If you're in an old release then it will be tied to everything.  In newer ones I've managed to get rid of it in both Hardy and Ibex.  without it killing the system.

---

### Post by jimv on 2008-11-06
> I can't uninstall evolution-data-server and evolution-data-server-common.

No, you can't uninstall evolution-data-server-common without remove those other programs.  Evolution-data-server should come off just fine though.  The other packages (gnome-panel, gnome-applets) depend on evolution-data-server-common.

---

### Post by druellan on 2008-11-08
Any idea from where evolution-data-server is invoked? I don't want to uninstall it but just disable it as much as possible, and data-server is no longer listed on the system-session.

---

