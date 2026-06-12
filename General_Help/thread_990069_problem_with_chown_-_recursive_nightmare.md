---
title: "problem with chown - recursive nightmare"
date: 2008-11-22
forum: General Help
---

### Post by andy_t on 2008-11-22
Hi,

I was sorting a few file issues with chown, basically using chown -R to take ownership of all the files that live on a shared partition. It was going fine until I accidentally let a /. slip into my code - don't know what the hell I was thinking.

Anyway as a rescue I chown'd back the whole filesystem to root:root (since it had changed to andy:andy), then chown'd my home area back to me. Now I have lost network access, and am thinking that I need to chown some files to other user/group combos.

Any way to rescue this major f**k-up?

Thanks in advance!

---

