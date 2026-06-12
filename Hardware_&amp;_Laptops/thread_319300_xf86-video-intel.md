---
title: "xf86-video-intel"
date: 2006-12-15
forum: Hardware &amp; Laptops
---

### Post by jrichardson on 2006-12-15
Hello,
Been hammering on this for a while. I have a machine with the integrated Intel video chipset.

After many hours of scouring and repeated efforts I cam across a How To install the latest Intel video drivers.

I have reached a stopping point about 80% the way through:

[B]jerry@jerry-desktop:~/src/xf86-video-intel$ git checkout modesetting fatal: [COLOR="Red"]cannot open index.lock file.[/COLOR]
jerry@jerry-desktop:~/src/xf86-video-intel$ sudo git checkout modesetting
[COLOR="Red"]git-checkout-index: modesetting is not in the cache[/COLOR]
jerry@jerry-desktop:~/src/xf86-video-intel$[/B]

Tried git pull to no avail

[B]jerry@jerry-desktop:~/src/xf86-video-intel$ git pull
[COLOR="Red"]fatal: Needed a single revision
Pulling into a black hole?[/COLOR]
jerry@jerry-desktop:~/src/xf86-video-intel$[/B]


Any ideas?

---

