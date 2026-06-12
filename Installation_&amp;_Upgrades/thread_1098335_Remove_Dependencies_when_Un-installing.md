---
title: "Remove Dependencies when Un-installing"
date: 2009-03-16
forum: Installation &amp; Upgrades
---

### Post by Spectre5 on 2009-03-16
I have a simple question...when I install something from the repos, there are often dependencies (obviously).  So lets say I install a program called AAA and it has 5 dependencies.  Then when I go to un-install the "AAA" program for whatever reason, Synaptic only un-installs AAA, but it does not un-install the 5 dependencies (obviously they are not required by anything else if the installation of AAA installed them and nothing else has been installed since).

So how do you make Synaptic remove everything, including dependencies?

Thanks,

---

### Post by zvacet on 2009-03-17
Mark package for total removal(maybe this is not exact but I don´t use English version;besides I think you will understand when you open synaptic).Other option is from terminal

```
sudo apt-get autoremove
```

---

### Post by Spectre5 on 2009-03-18
> **zvacet said:**
> Mark package for total removal(maybe this is not exact but I don´t use English version;besides I think you will understand when you open synaptic).Other option is from terminal

```
sudo apt-get autoremove
```

I do mark the package for "complete removal" but it still only removes the one package, not the dependencies.  I'll try the terminal method next time, thanks.

Any other ideas through synaptic?

---

### Post by Spectre5 on 2009-03-18
> **Spectre5 said:**
> I do mark the package for "complete removal" but it still only removes the one package, not the dependencies.  I'll try the terminal method next time, thanks.

Any other ideas through synaptic?

Looks like these packages end up in Status -> Installed (auto-removable).  I think this is what the previous poster mentioned using the terminal.

But still, is there a way to remove them at the same time you un-install another package?

---

### Post by zvacet on 2009-03-18
>   autoremove
           autoremove is used to remove packages that were automatically
           installed to satisfy dependencies for some package and that are no
           more needed.


Look in **man apt-get**

---

