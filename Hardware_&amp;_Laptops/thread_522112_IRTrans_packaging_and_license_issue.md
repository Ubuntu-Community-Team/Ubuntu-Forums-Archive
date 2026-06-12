---
title: "IRTrans packaging and license issue"
date: 2007-08-10
forum: Hardware &amp; Laptops
---

### Post by bozr on 2007-08-10
Hi everyone,

Sorry if this in the wrong subforum, but I didn't find a more suitable one.

I'm in the process of packaging the IRTrans IR transceiver software for Ubuntu. IRTrans offers a lircd compatible server for their hardware that is freely available for Linux (including source code).

Unfortunately the IRTrans source code is currently distributed without an accompanying license. Since the Ubuntu policy requires a license to be shipped with the package, I've had some very constructive discussions with the guys from IRTrans. Basically they are willing to license their code under an opensource compatible license. Initially they came up with GPL, but the source code contains a not open binary blob containing device firmware, which is linked into the final executable. This makes GPL a no-go. So, now they're a bit lost on what license to use.

I'm also not really into the licensing subject, so what would be a suitable alternative here? LGPL seems to be suitable for libraries, but the code is not really a libreary. BSD might also be an option. Any other suggestions?

Thanks,
Ruud

---

