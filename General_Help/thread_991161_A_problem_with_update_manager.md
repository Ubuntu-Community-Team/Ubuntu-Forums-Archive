---
title: "A problem with update manager"
date: 2008-11-23
forum: General Help
---

### Post by bob74 on 2008-11-23
I have looked at other posts relating to update manager problems but haven't found similar. On updating I get the following:

W: Failed to fetch [http://playonlinux.botux.net/dists/hardy/Release.gpg](http://playonlinux.botux.net/dists/hardy/Release.gpg)  Could not resolve ‘playonlinux.botux.net’

W: Failed to fetch [http://playonlinux.botux.net/dists/hardy/main/i18n/Translation-en_GB.bz2](http://playonlinux.botux.net/dists/hardy/main/i18n/Translation-en_GB.bz2)  Could not resolve ‘playonlinux.botux.net’

W: Some index files failed to download, they have been ignored, or old ones used instead.
Can some kind person help me to resolve this which, incidentally , is the only glitch I have experienced with Hardy.
Thanking you in anticipation.
bob74

---

### Post by ajgreeny on 2008-11-23
Those links do not go anywhere, that is the problem.  Perhaps the servers are down temporarily, or even permanently, because clicking gives an "Address not found" error in firefox.  If firefox can't find it, Update manager won't either.

---

