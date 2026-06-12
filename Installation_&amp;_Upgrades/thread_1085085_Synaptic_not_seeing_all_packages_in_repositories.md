---
title: "Synaptic not seeing all packages in repositories"
date: 2009-03-02
forum: Installation &amp; Upgrades
---

### Post by sehrgut on 2009-03-02
Recently Synaptic has been acting oddly (apt too . . . this problem sometimes persists to apt-get), in that it won't list all packages available in some repos. It sees the repos correctly (because some packages will be listed under Origin > [reponame]), but won't show all of them. As well, the package lists in /var/lib/apt/lists are there (and updated when I force an update in the GUI), but really don't contain references to these packages -- like they're being dropped during parsing.

I first noticed this with my local trivial repo ("deb file:/media/repo deb32/") I use for propagating updates to offline machines (simply by rsync'ing my apt caches to it with a script that then rebuilds its Packages.gz file). Occasionally some of the debs I'd drop in there wouldn't be available after regenerating the Packages.gz and refreshing Synaptic.

It really came to a head when Synaptic wasn't seeing Opera in the Canonical Partner repo. For good measure I added the three other intrepid dists on their server, but of course those repos are actually empty: there for symmetry with the main Ubuntu repos, I'd imagine.

deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) intrepid partner
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) intrepid-updates partner
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) intrepid-security partner
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) intrepid-backports partner

No such luck.

Occasionally such packages will be available via apt-get install on the command line, but not this time. I'm completely befuddled. Anyone else seen something similar?

---

### Post by sehrgut on 2009-03-04
Okay, turns out the Opera thing isn't a case of this problem: I grabbed all the Packages.gz files from the Partner repo, and even though the Opera debs are still in the pool, they're not listed as part of any release. *shrugs* I guess the Opera repos are where we're supposed to go for that now.

However, this still happens. For instance, I wanted to install WINE last week, and wasn't showing up, even though I could grep through the cached Packages files and see it. Now, for whatever reason -- it must be POM-dependent -- it was visible in Synaptic.

Wine was always visible using apt-cache search, so why Synaptic wouldn't see it, across numerous refreshes and updates, is beyond me.

---

