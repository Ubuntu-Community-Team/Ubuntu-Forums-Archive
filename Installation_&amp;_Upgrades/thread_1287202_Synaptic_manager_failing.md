---
title: "Synaptic manager failing"
date: 2009-10-09
forum: Installation &amp; Upgrades
---

### Post by allbhatias on 2009-10-09
Hi

When i start Synaptic package manager, i also click on reload
and then i get the error as follows

[I]"GPG error: [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) jaunty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 58403026387EE263Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/jaunty/main/binary-i386/Packages](http://in.archive.ubuntu.com/ubuntu/dists/jaunty/main/binary-i386/Packages)  404 Not Found
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/jaunty/restricted/binary-i386/Packages](http://in.archive.ubuntu.com/ubuntu/dists/jaunty/restricted/binary-i386/Packages)  404 Not Found
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/jaunty/main/source/Sources](http://in.archive.ubuntu.com/ubuntu/dists/jaunty/main/source/Sources)  404 Not Found
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/jaunty/restricted/source/Sources](http://in.archive.ubuntu.com/ubuntu/dists/jaunty/restricted/source/Sources)  404 Not Found
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/jaunty/universe/binary-i386/Packages](http://in.archive.ubuntu.com/ubuntu/dists/jaunty/universe/binary-i386/Packages)  404 Not Found
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/jaunty/universe/source/Sources](http://in.archive.ubuntu.com/ubuntu/dists/jaunty/universe/source/Sources)  404 Not Found
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/jaunty/multiverse/binary-i386/Packages](http://in.archive.ubuntu.com/ubuntu/dists/jaunty/multiverse/binary-i386/Packages)  404 Not Found
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/jaunty/multiverse/source/Sources](http://in.archive.ubuntu.com/ubuntu/dists/jaunty/multiverse/source/Sources)  404 Not Found
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/jaunty-updates/main/binary-i386/Packages](http://in.archive.ubuntu.com/ubuntu/dists/jaunty-updates/main/binary-i386/Packages)  404 Not Found
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/jaunty-updates/restricted/binary-i386/Packages](http://in.archive.ubuntu.com/ubuntu/dists/jaunty-updates/restricted/binary-i386/Packages)  404 Not Found
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/jaunty-updates/main/source/Sources](http://in.archive.ubuntu.com/ubuntu/dists/jaunty-updates/main/source/Sources)  404 Not Found
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/jaunty-updates/restricted/source/Sources](http://in.archive.ubuntu.com/ubuntu/dists/jaunty-updates/restricted/source/Sources)  404 Not Found
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/jaunty-updates/universe/binary-i386/Packages](http://in.archive.ubuntu.com/ubuntu/dists/jaunty-updates/universe/binary-i386/Packages)  404 Not Found
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/jaunty-updates/universe/source/Sources](http://in.archive.ubuntu.com/ubuntu/dists/jaunty-updates/universe/source/Sources)  404 Not Found
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/jaunty-updates/multiverse/binary-i386/Packages](http://in.archive.ubuntu.com/ubuntu/dists/jaunty-updates/multiverse/binary-i386/Packages)  404 Not Found
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/jaunty-updates/multiverse/source/Sources](http://in.archive.ubuntu.com/ubuntu/dists/jaunty-updates/multiverse/source/Sources)  404 Not Found
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/jaunty-backports/main/binary-i386/Packages](http://in.archive.ubuntu.com/ubuntu/dists/jaunty-backports/main/binary-i386/Packages)  404 Not Found
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/jaunty-backports/restricted/binary-i386/Packages](http://in.archive.ubuntu.com/ubuntu/dists/jaunty-backports/restricted/binary-i386/Packages)  404 Not Found
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/jaunty-backports/universe/binary-i386/Packages](http://in.archive.ubuntu.com/ubuntu/dists/jaunty-backports/universe/binary-i386/Packages)  404 Not Found
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/jaunty-backports/multiverse/binary-i386/Packages](http://in.archive.ubuntu.com/ubuntu/dists/jaunty-backports/multiverse/binary-i386/Packages)  404 Not Found
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/jaunty-backports/main/source/Sources](http://in.archive.ubuntu.com/ubuntu/dists/jaunty-backports/main/source/Sources)  404 Not Found
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/jaunty-backports/restricted/source/Sources](http://in.archive.ubuntu.com/ubuntu/dists/jaunty-backports/restricted/source/Sources)  404 Not Found
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/jaunty-backports/universe/source/Sources](http://in.archive.ubuntu.com/ubuntu/dists/jaunty-backports/universe/source/Sources)  404 Not Found
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/jaunty-backports/multiverse/source/Sources](http://in.archive.ubuntu.com/ubuntu/dists/jaunty-backports/multiverse/source/Sources)  404 Not Found
Some index files failed to download, they have been ignored, or old ones used instead."[/I]

ANY IDEA WHAT SHOULD I DO?

---

### Post by 10Digits on 2009-10-10
what was the software that you downloaded??or what did you add to the sources list??


The problem is that there is no public key for the software source you might have added in the sources list.


I think you should go to the software sources and disable the software source or go to the site and search for the PGP key.

---

### Post by jrev on 2009-10-15
Hi all,

What is the exact command you should pass in command line to get the key installed ?

I have been looking around without any success.

Thanks for your proper advice :P

---

### Post by garvinrick4 on 2009-10-15
Look in System/Admin/software sources/    Authentacation tab    

It will tell you what keys you need.  Wine is one. 

Ubuntu repositories have an automatic signing key.  Should be there.

Any key you need just google the repository you need. Copy the key and paste in Terminal.

Exept for wine they are all Ubuntu.

---

