---
title: "Magic Set Editor"
date: 2009-07-21
forum: Installation &amp; Upgrades
---

### Post by KingAlanI on 2009-07-21
magicseteditor.sourceforge.net

Doesn't seem to have a package in the repo (please correct me if I'm wrong), so I go to sourceforge to get the .tar.gz
Believe this is a binaries tarball, not a source tarball.

I open the Large version .tar.gz with Archive Manager, and get this:

gzip: stdin: not in gzip format
tar: Child returned status 1
tar: Error exit delayed from previous errors

---

### Post by link on 2009-09-20
For version 0.3.8, the version that's available as of this writing, the file is actually just a GNU tar archive, not a gzipped, tar archive (as the filename implies). Rename the file from *.tar.gz to *.tar and then you'll be able to unarchive it.

You'll also need to install libwxgtk2.8-0 in order to run it.

---

