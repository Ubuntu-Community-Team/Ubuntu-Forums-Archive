---
title: "firefox3 shows &quot;tab&quot; instead of space"
date: 2008-09-10
forum: General Help
---

### Post by Niosus on 2008-09-10
i've had this problem since the first alpha release of firefox 3, i tried uninstalling(completly) it and reinstalling but it doesn't work. Now the final version is released i want to get this solved but couldn't find anything about it.

The main problem is that a "space" is showed like a tab

|_| in FF2 shows as |____| in FF3

example is in attachment.


Could anyone please help me? it's kind of annoying

---

### Post by y-lee on 2008-09-10
There is a bug report about this or a related problem on [Launchpad]("https://bugs.launchpad.net/ubuntu/+source/firefox-3.0/+bug/193108"), a solution seems to be :

> The culprit appears to be the pango-graphite package. If I purge it, the Exceptions and spacing bugs go away, suggesting that Firefox has no clue how to deal with the Graphite extensions to TrueType/OpenType fonts.

---

