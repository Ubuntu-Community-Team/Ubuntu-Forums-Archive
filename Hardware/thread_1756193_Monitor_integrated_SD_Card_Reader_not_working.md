---
title: "Monitor integrated SD Card Reader not working"
date: 2011-05-12
forum: Hardware
---

### Post by ashughes on 2011-05-12
Hi,

I have a DELL LCD monitor (U2711) with an integrated SD Card reader. It does not automount the SD Card. I've not tried manually mounting it, but I'm not sure how to do that.

I've run dmesg and I don't see a SDHCI device coming up either, so maybe the problem is the reader is not being picked up?

$ dmesg | grep sdhci
[ 3183.825992] sdhci: Secure Digital Host Controller Interface driver
[ 3183.825994] sdhci: Copyright(c) Pierre Ossman
$

Does anyone have any ideas how I can get this working?

FYI, I'm using Ubuntu 11.04 64-bit.

---

### Post by frogotronic on 2012-05-04
I have the same problem with a 2405FPW monitor and 10.04.4 LTS

No solution as of yet.

---

