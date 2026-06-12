---
title: "Graphics drivers manual install"
date: 2013-06-14
forum: Hardware
---

### Post by Isaacmarritt on 2013-06-14
I have tried to install drivers using the Intel graphics drivers program [https://01.org/linuxgraphics/](https://01.org/linuxgraphics/) but it said this
```

W: GPG error: https://download.01.org Ubuntu Release:
 The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 8D8847D52F4AAA66

```
I have tried ways to fix this but  they have not worked does anyone know how to to install GPU driver manually. Also witch drivers I need form this list [https://01.org/linuxgraphics/downloads](https://01.org/linuxgraphics/downloads) .
Thank you

---

### Post by deadflowr on 2013-06-14
Look at the[ X crackers]("https://launchpad.net/~xorg-edgers/+archive/ppa").

or the more stable [xswat-xupdates]("https://launchpad.net/~ubuntu-x-swat/+archive/x-updates")

---

### Post by Yellow Pasque on 2013-06-14
With Ubuntu 13.04, the best intel drivers come pre-installed. xorg-edgers might have a newer version, but I wouldn't expect any drastic changes compared to stock 13.04 drivers.

> or the more stable xswat-xupdates
That PPA is fairly outdated and doesn't even have any packages for Raring/13.04

---

