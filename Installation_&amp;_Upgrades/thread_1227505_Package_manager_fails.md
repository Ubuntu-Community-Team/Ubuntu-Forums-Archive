---
title: "Package manager fails"
date: 2009-07-30
forum: Installation &amp; Upgrades
---

### Post by krauser530 on 2009-07-30
So I was attempting to uninstall/reinstall firefox when synaptic crashed. I get the following message now whenever I try to use apt-get or synaptic:

(Reading database ... 239728 files and directories currently installed.)
Removing firefox ...
Setting up firefox-3.0 (3.0.1 +build1nobinonly-0ubuntu0.9.04.1) ...
dpkg (subprocess): unable to execute post-installation script: Exec format error
dpkg: error processing firefox-3.0 (--configure):
 subprocess post-installation script returned error exit status 2
Errors were encountered while processing:
 firefox-3.0
E: Sub-process /usr/bin/dpkg returned an error code (1)

Any ideas on how to fix?

---

### Post by dstew on 2009-07-31
I think this is a bug in the dpkg system. See [this thread]("http://ubuntuforums.org/showthread.php?t=1206227&highlight=manually+remove+package&page=2"). There are two ways to get around it. One, you can remove the old (broken) package manually; two, you can install a module borrowed from another Debian distribution that seems to work. Both methods are outlined at the end of the thread.

---

