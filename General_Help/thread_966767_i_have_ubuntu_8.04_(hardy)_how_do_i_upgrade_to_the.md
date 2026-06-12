---
title: "i have ubuntu 8.04 (hardy) how do i upgrade to the new one?"
date: 2008-11-01
forum: General Help
---

### Post by reinaldistic on 2008-11-01
i wanna upgrade, is there a way to do it without downloading the live cd all over again and installing it?, just like updating my current version of ubuntu?

---

### Post by dburnett77 on 2008-11-01
> **reinaldistic said:**
> i wanna upgrade, is there a way to do it without downloading the live cd all over again and installing it?, just like updating my current version of ubuntu?

as sudo or su, "apt-get upgrade"

and you might want to run sudo apt-get update before, this will update the repositories which have changed.

---

### Post by Glubbdubdribian on 2008-11-01
Hi. go into system>Administration>Software sources. Then go to the updates tab and at the very bottom choose "normal releases" rather than "long term support releases only". Then go to the update manager and update from there.

---

### Post by Glubbdubdribian on 2008-11-01
oops - got to me before it. and yh the command line way is much easier - they didn't mention that on the ubuntu guide :(
oh well...

---

