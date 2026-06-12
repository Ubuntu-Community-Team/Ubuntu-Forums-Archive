---
title: "Update Manager Problem"
date: 2009-03-09
forum: Installation &amp; Upgrades
---

### Post by QuickNinja on 2009-03-09
Hey everyone I'm fairly new to Ubuntu and I have encountered a problem with the update manager.  It seems that every time I go to update it won't let me.  It has the triangle in the icon notifier.

It gives me this error when I type "sudo apt-get update" 

W: GPG error: [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) intrepid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 58403026387EE263
W: GPG error: [http://deb.mulx.net](http://deb.mulx.net) hardy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY B1F5957DE4946268
W: Failed to fetch [http://nz.archive.ubuntu.com/ubuntu/dists/intrepid-security/Release](http://nz.archive.ubuntu.com/ubuntu/dists/intrepid-security/Release)  Unable to find expected entry  [http://www.openoffice.de/wt/winetools-0.9jo-III.tar.gz/source/Sources](http://www.openoffice.de/wt/winetools-0.9jo-III.tar.gz/source/Sources) in Meta-index file (malformed Release file?)

E: Some index files failed to download, they have been ignored, or old ones used instead.


Any suggestions on fixing this problem? I've selected other sources from software sources and no luck.

---

### Post by Neo_The_User on 2009-03-09
You need the Scott Richie GPG key.

[http://www.winehq.org/download/deb](http://www.winehq.org/download/deb)

Follow that guide.

---

### Post by QuickNinja on 2009-03-10
Yeah I added the key and no luck in fixing the problem.

Here's sudo apt-get update again if anything changed.

W: GPG error: [http://deb.mulx.net](http://deb.mulx.net) hardy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY B1F5957DE4946268
W: Failed to fetch [http://nz.archive.ubuntu.com/ubuntu/dists/intrepid-security/Release](http://nz.archive.ubuntu.com/ubuntu/dists/intrepid-security/Release)  Unable to find expected entry  [http://www.openoffice.de/wt/winetools-0.9jo-III.tar.gz/source/Sources](http://www.openoffice.de/wt/winetools-0.9jo-III.tar.gz/source/Sources) in Meta-index file (malformed Release file?)

E: Some index files failed to download, they have been ignored, or old ones used instead.

---

