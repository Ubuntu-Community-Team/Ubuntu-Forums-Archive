---
title: "Scanner doesn't work after the upgrade"
date: 2011-12-19
forum: Hardware
---

### Post by huntkey on 2011-12-19
Hi experts,

I actually have already posted my question in the "General Help" category. It might be wrong place for this question... Anyway...

So after the upgrade from 11.04 to 11.10 my scanner doesn't work any more...

It is Samsung SCX-4521F. It is multi-purpose printer. The printing part works fine so the USB connection should be good.

sane-find-scanner tool can see the scanner:

```
found USB scanner (vendor=0x04e8 [Samsung], product=0x3419 [SCX-4x21 Series]) at libusb:007:007
```I was searching on the Sane scanner website and I only found SCX-4500 as supported scanner. I don't know if 4521F is one of them or not. However it was definitely working before.

I also tried to edit "xerox_mfp.conf" file by adding the following to the bottom but still no luck.

```
#Samsung SCX-4521F
usb 0x04e8 0x3419
```

I'm really out of ideas... It's really important to me. Please help! Thanks a bunch!

---

### Post by Joshas on 2012-05-08
Did you managed to solve your issue? I see post marked as SOLVED, but no solution.

---

### Post by dr_smit on 2013-02-03
Try visiting for solution
[http://www.bchemnet.com/suldr/forum/index.php?topic=46.0](http://www.bchemnet.com/suldr/forum/index.php?topic=46.0)

---

