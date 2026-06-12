---
title: "Upgrade to jaunty:  traker indexing no longer works."
date: 2009-04-30
forum: Installation &amp; Upgrades
---

### Post by danebramaged on 2009-04-30
Traker applet:  There was an error while performing indexing:  Reindex all contents, Cancel, Ok.

No matter what I click on, the error message does not go away.  So far my only option is to kill the process and not use tracker for indexing at all.  

If anyone else has encountered this problem, please let me know if you have a solution.



(  I have had so many problems with Jaunty in the first few hours that I think we should change it's name to "ABORT RETRY IGNORE"  )

---

### Post by cariboo on 2009-04-30
Just remove the tracker cache in your home directory and reindex. This is a common problem, there have been many questions about the same problem. It is a hidden file, so you will have to open nautilus and press Ctrl-h to reveal the hidden files and directories.

---

### Post by danebramaged on 2009-04-30
/home/isaac/.cache/traker deleted.  Re-indexing now.  Only an hour more to go and I'll be able to tell you if this works.  

Let's all keep our fingers crossed.

---

### Post by DavidTangye on 2009-05-01
See the launchpad bug reports [including this one]("https://bugs.launchpad.net/ubuntu/+source/tracker/+bug/346912").

---

### Post by danebramaged on 2009-05-01
traker seems to work now.  Of course I've found more problems since, but that will be a seperate thread.

---

