---
title: "ClamAv update issues Debian key?"
date: 2009-03-29
forum: Installation &amp; Upgrades
---

### Post by swiftwood on 2009-03-29
Hello

When I went to update my virus signatures I got the following

> sudo freshclam
ClamAV update process started at Sun Mar 29 17:41:24 2009
WARNING: Your ClamAV installation is OUTDATED!
WARNING: Local version: 0.94.2 Recommended version: 0.95
DON'T PANIC! Read [http://www.clamav.net/support/faq](http://www.clamav.net/support/faq)
main.cld is up to date (version: 50, sigs: 500667, f-level: 38, builder: sven)
daily.cld is up to date (version: 9180, sigs: 37728, f-level: 41, builder: guitar)


I then tried updating ClamAV and got the following

> 
*sudo apt-get update*
...
Fetched 190B in 2s (74B/s)
Reading package lists... Done
W: GPG error: [http://volatile.debian.org](http://volatile.debian.org) etch/volatile Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY EC61E0B0BBE55AB3
W: You may want to run apt-get update to correct these problems


The update worked last time, I don't see why I would need a new key.

---

### Post by garyedwardjohnston on 2009-04-28
keys expire in time...u will need a new one

---

