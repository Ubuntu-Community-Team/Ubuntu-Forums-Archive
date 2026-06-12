---
title: "How can you view available updates on server builds?"
date: 2009-10-23
forum: Installation &amp; Upgrades
---

### Post by filfish on 2009-10-23
Hi All

I'm beginning to find my way around my ubuntu 8.04 servers now, but on thing that still gets me is updates!

I can run updates and upgrades, but I was wondering if there is a way to view the available updates and choosing which ones to install?

On my desktop system, i get a popup with all the available updates and I can choose which ones to install and which ones to leave off (if required), now I don't expect a pop up box on my server build! but it would be good if there was a command to show the available ones such as

:~# apt-get list-updates

according to the man pages,

:~# apt-get --show-upgraded 
or
:~# apt-get -u

should give me the desired result but I can't get anything from it!

back to the noob corner, I know!!

Cheers
should

---

### Post by earthpigg on 2009-10-23
hi,

[http://linux.die.net/man/8/apt-get](http://linux.die.net/man/8/apt-get)
(or type 'man apt-get')
```
-s
--simulate
--just-print
--dry-run
--recon
--no-act
    No action; perform a simulation of events that would occur but do not actually change the system. Configuration Item: APT::Get::Simulate.

    Simulate prints out a series of lines each one representing a dpkg operation, Configure (Conf), Remove (Remv), Unpack (Inst). Square brackets indicate broken packages with and empty set of square brackets meaning breaks that are of no consequence (rare).
```

try tossing the -s option into the mix.

```
sudo apt-get -s upgrade
```

---

