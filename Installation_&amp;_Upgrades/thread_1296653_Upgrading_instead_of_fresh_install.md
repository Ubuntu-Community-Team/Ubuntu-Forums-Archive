---
title: "Upgrading instead of fresh install"
date: 2009-10-20
forum: Installation &amp; Upgrades
---

### Post by daldude on 2009-10-20
Is it possible to upgrade an older version of Ubuntu to a newer version as apposed to reinstalling from scratch and losing all ones customized setting and having to reinstall all your programs?
Can a 32-bit version be upgraded to a 64-bit version?
I want to get 9.10 64-bit when it goes official but right now have 8.4 32-bit. Will I be able to upgrade my 8.04 32-bit to 9.10 64-bit or do I have to do a fresh install?:)

---

### Post by earthpigg on 2009-10-20
migrating from one architecture to another (32 to 64 bit), you will always have to do a fresh install.

to keep your personal settings and migrate them forward:

back up your /home/your-username/ and restore the contents of that folder on the fresh install.

to explore how this works:

in the file manager (nautilus) select view -> show hidden files.

dig around the files and folder starting with a dot (.). those are 'dotfiles' and contain all your settings for different programs.

---

