---
title: "wubi download over 40 hours, extremely slow"
date: 2009-04-26
forum: Installation &amp; Upgrades
---

### Post by pieguy on 2009-04-26
I was trying out the wubi installer and it says it will be done in 40+ hours, so I gave up.  Is that normal or is this just because of increased traffic for 9.04?  I think an installer that has to fetch files is not such a good idea, you should host the whole think that way it can be downloaded in a download manager and mirrored on other sites and installed when you have it all.

---

### Post by pytheas22 on 2009-04-26
It's probably just slow because the Ubuntu servers are overloaded right now.

A way to work around this would be to download the Ubuntu live CD .iso file using a torrent (which should be much faster than trying to use the servers), move it into the same directory as wubi.exe, and run wubi again.  wubi should automatically detect the Ubuntu .iso and use that for the installation, rather than downloading everything from the Internet.  If wubi doesn't recognize the .iso, I think you can run it from the command-line with an argument telling it to use the .iso; check the wubi website for the syntax.

---

