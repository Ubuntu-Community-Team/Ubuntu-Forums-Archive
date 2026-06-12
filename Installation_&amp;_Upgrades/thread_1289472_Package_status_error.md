---
title: "Package status error"
date: 2009-10-12
forum: Installation &amp; Upgrades
---

### Post by lingenfr on 2009-10-12
OK, I installed Netbook Remix on an 8GB SD for my wife's EEE PC (700). The install went fine. I started adding some of the essentials apps and add-ons to FF. I was in the middle of this and the battery failed. When I plugged back in and fired it up, I had the DO NOT ENTER sign saying there was a problem with dependencies. I assumed that something had been corrupted, so I rebooted and went into recovery mode and ran fsck. Many, many errors, but fsck completed. When I rebooted, same problem. When I run any apt, dpkg, etc. I get errors similar to:

E: Problem parsing dependency Depends
E: Error occurred while processing mono-2.0-gac (NewVersion1)
E: Problem with MergeList /var/lib/dpkg/status
E: The package lists or status file could not be parsed or opened.

I searched and found a couple of ideas, but:

sudo apt-get -f install
sudo dpkg --configure -a

and moving the status file and restoring an old version did not work. I am assuming that I will have to start over and reinstall, but wanted to check first. I am also noting some odd (but maybe unrelated) behaviors such as FF not enabling the Back button. Any ideas?

---

