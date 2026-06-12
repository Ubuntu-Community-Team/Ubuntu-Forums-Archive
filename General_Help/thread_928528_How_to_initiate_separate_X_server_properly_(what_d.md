---
title: "How to initiate separate X server properly (what do all these options mean?)"
date: 2008-09-24
forum: General Help
---

### Post by Ng Oon-Ee on 2008-09-24
Hi all,

Been trying to startup a separate X server for running games through wine. Everytime I do that, my original X server restarts itself (everything closes forcibly, I have to login again) and my game doesn't show.

This request really has nothing to do with wine, as this is not the correct forum. I'd just like to know what all those options are when running X or xinit or the like. The man pages seem quite uninformative, specifically for X.

The line I'm having problems with is:-

X :3 -ac -terminate & nvidia-settings --load-config-only

When I run this, it does start up a separate server (the NVidia logo shows) but it also restarts my own. And the other server doesn't have a WM I believe, so I can't seem to run anything on it either.

Any help appreciated. Apologies if my explanations aren't enough, please let me know if more details needed.

---

