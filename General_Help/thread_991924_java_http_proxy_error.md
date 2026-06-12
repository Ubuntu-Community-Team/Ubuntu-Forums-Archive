---
title: "java http proxy error?"
date: 2008-11-24
forum: General Help
---

### Post by moore.bryan on 2008-11-24
is anyone else getting an error with java (1.6.0.10) when running through a proxy? it keeps telling me http is an unknown proxy type. i've searched and found *some* discussion of a similar problem on the sun developer's forum, but it's not exactly the same *and* it is with a much older version of java.

any insight would be appreciated.

okay, so inexplicably and in no way explainable, everything's solved itself to some extent. now i can get the jnlp file to load and make changes to the "document," even though it tells me i can't and there's been an error, there isn't and everything works. i won't mark the thread as "solved" though because it isn't, just triaged for me.

---

### Post by rakeleer on 2009-03-02
Seems to be somehow related to socket connections in some java apps, and the proxy being enabled, at all.

We have the same problem.  Java 1.6+Powerschool java based gradebook = fail.

Unfortunately, the only solution I've found is to disable the proxy settings in Java, which breaks it for everything outside of our LAN.

For now, I guess we try and stick with 1.5.

---

### Post by moore.bryan on 2009-03-02
> **rakeleer said:**
> Seems to be somehow related to socket connections in some java apps, and the proxy being enabled, at all.

We have the same problem.  Java 1.6+Powerschool java based gradebook = fail.

Unfortunately, the only solution I've found is to disable the proxy settings in Java, which breaks it for everything outside of our LAN.

For now, I guess we try and stick with 1.5.
sounds exactly the same; like i wrote above, though, i seem to have pseudo-fixed the issue. i logged-in at home *without* the proxy set and when i was in-school, i had no issues.

---

