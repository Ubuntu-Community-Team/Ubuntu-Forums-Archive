---
title: "Hardware crypto"
date: 2010-08-08
forum: Hardware
---

### Post by Kurlon on 2010-08-08
I can't seem to find the hifn crypto engine for OpenSSL to support my Hi/Fn crypto card I've got in my Soekris 4801.

I see the following in my dmesg:

[   50.809882] hifn795x: assuming 66MHz clock speed, override with hifn_pll_ref=ext<frequency>
[   51.460223] hifn0: AES 128 ECB test has been successfully passed.
[   51.504255] alg: No test for cfb(des3_ede) (cfb-3des-hifn0)
[   51.564253] alg: No test for ofb(des3_ede) (ofb-3des-hifn0)
[   51.737110] alg: No test for cfb(des) (cfb-des-hifn0)
[   51.810988] alg: No test for ofb(des) (ofb-des-hifn0)
[   52.292238] alg: No test for cfb(aes) (cfb-aes-hifn0)
[   52.348226] alg: No test for ofb(aes) (ofb-aes-hifn0)
[   52.349215] Driver for HIFN 795x crypto accelerator chip has been successfully registered.

So the card is being seen by the kernel.  Probing OpenSSL I don't see support available:

root@goliath:/usr/lib/ssl# openssl engine
(padlock) VIA PadLock (no-RNG, no-ACE)
(dynamic) Dynamic engine loading support

apt-cache search hifn doesn't yield any hits either.  Suggestions?

---

