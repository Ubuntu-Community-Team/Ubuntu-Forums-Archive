---
title: "Extremely slow after todays openssl update on 8.10"
date: 2009-06-26
forum: Installation &amp; Upgrades
---

### Post by blirp on 2009-06-26
I updated openssl and friends today, as suggested by the upgrade manager:
libssl-dev (0.9.8g-10.1ubuntu2.2) to 0.9.8g-10.1ubuntu2.4
libssl0.9.8 (0.9.8g-10.1ubuntu2.2) to 0.9.8g-10.1ubuntu2.4
openssl (0.9.8g-10.1ubuntu2.2) to 0.9.8g-10.1ubuntu2.4
thunderbird (2.0.0.21+nobinonly-0ubuntu0.8.10.1) to 2.0.0.22+build1+nobinonly-0ubuntu0.8.10.1

The resulting system is extremely slow. Starting up a Jaunty in a VirtualBox takes forever, and uses 100% CPU. 
Also things like update-apt-xapian-index and apt-check uses 100% CPU for extended periods of time.

All this worked nicely yesterday, so I believe the SSL-update is to blame (I'm currently not running thunderbird).

Has anyone else seen this?
Is there any way to downgrade the SSL-library to get back a working machine?

M.

---

