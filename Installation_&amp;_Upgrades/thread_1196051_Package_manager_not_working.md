---
title: "Package manager not working"
date: 2009-06-24
forum: Installation &amp; Upgrades
---

### Post by pib712 on 2009-06-24
Hi, I just tried to start up Synaptic and got the following error message:

E: Dynamic MMap ran out of room
E: Error occurred while processing libfli-dev (NewVersion1)
E: Problem with MergeList /var/lib/apt/lists/uk.archive.ubuntu.com_ubuntu_dists_jaunty_universe_binary-i386_Packages
E: The package lists or status file could not be parsed or opened.
E: _cache->open() failed, please report.

When trying to install a package from the terminal with apt-get, I get the same message. I've searched around and there's some similar problems which seem to have vastly different solutions. To my knowledge I've not recently installed any packages or updates that could have caused this - it seems to have just come out of nowhere. Does anyone have any ideas? Thanks.

---

### Post by pib712 on 2009-06-25
Never mind - seems it's solved now. I just used "sudo apt-get update" and "sudo apt-get install -f". Should have been among the first things I tried really.

---

