---
title: "how do I make a package?"
date: 2008-08-14
forum: General Help
---

### Post by &amp;)ky#)^ on 2008-08-14
Here's what I want to do.  I want to make a binary package from the Nestopia source code for Linux.  It is super easy to build perfect packages for programs that include .diff.gz and .dsc files.  However, this project has no such thing.  I would use checkinstall, except that I really don't care for the metadata that it creates for the .deb packages.  I much prefer using dpkg-source and dpkg-buildpackage.

Since Nestopia doesn't have diffs or dsc files, how might I create them to support my package?

---

### Post by sdennie on 2008-08-14
I was going to respond to this with "Use checkinstall" but, it sounds like you aren't keen on that.  Maybe check: [http://ubuntuforums.org/showthread.php?t=51003](http://ubuntuforums.org/showthread.php?t=51003)

---

### Post by &amp;)ky#)^ on 2008-08-14
I saw that guide before and thought it mighty strange based on its wording, but I'll give it a try.

---

