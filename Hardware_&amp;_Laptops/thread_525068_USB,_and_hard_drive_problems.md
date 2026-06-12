---
title: "USB, and hard drive problems"
date: 2007-08-13
forum: Hardware &amp; Laptops
---

### Post by shockingelk on 2007-08-13
No USB device is recognized. I get a lot of freezes which usually start by the front window becoming unresponsive, then top and bottom panels disappearing, then just the orange background. Have to hold down the power key. This happens for both 6.10 and 7.04, with updates. Also tried the 64 bit version of 7.04. It's a Acer 5100.

thanks.

dmesg:
```
[   23.572000] hda_codec: invalid dep_range_val 0:7fff
[   23.572000] hda_codec: invalid dep_range_val 0:7fff
[   23.572000] hda_codec: invalid dep_range_val 0:7fff
[   23.572000] hda_codec: invalid dep_range_val 0:7fff
[   23.572000] hda_codec: invalid dep_range_val 0:7fff
[   23.572000] hda_codec: invalid dep_range_val 0:7fff
[   23.572000] hda_codec: invalid dep_range_val 0:7fff
[   23.572000] hda_codec: invalid dep_range_val 0:7fff
[   23.572000] hda_codec: invalid dep_range_val 0:7fff
[   23.572000] hda_codec: invalid dep_range_val 0:7fff
[   23.572000] hda_codec: invalid dep_range_val 0:7fff
[   23.572000] hda_codec: invalid dep_range_val 0:7fff
[   23.572000] hda_codec: invalid dep_range_val 0:7fff
[   23.572000] hda_codec: invalid dep_range_val 0:7fff
[   23.572000] hda_codec: invalid dep_range_val 0:7fff
[   23.572000] hda_codec: invalid dep_range_val 0:7fff
[   23.572000] hda_codec: invalid dep_range_val 0:7fff
[   23.572000] hda_codec: invalid dep_range_val 0:7fff
[   23.572000] hda_codec: invalid dep_range_val 0:7fff
[   23.572000] hda_codec: invalid dep_range_val 0:7fff
[   23.572000] hda_codec: invalid dep_range_val 0:7fff
[   23.572000] hda_codec: invalid dep_range_val 0:7fff
[   23.572000] hda_codec: invalid dep_range_val 0:7fff
[   23.572000] hda_codec: invalid dep_range_val 0:7fff
[   23.572000] hda_codec: invalid dep_range_val 0:7fff
[   23.572000] hda_codec: invalid dep_range_val 0:7fff
[   23.572000] hda_codec: invalid dep_range_val 0:7fff
[   23.572000] hda_codec: invalid dep_range_val 0:7fff
[   23.572000] hda_codec: invalid dep_range_val 0:7fff
[   23.572000] hda_codec: invalid dep_range_val 0:7fff
[   23.572000] hda_codec: invalid dep_range_val 0:7fff
[   23.572000] hda_codec: invalid dep_range_val 0:7fff
[   23.572000] hda_codec: invalid dep_range_val 0:7fff
[   23.572000] hda_codec: invalid dep_range_val 0:7fff
[   23.572000] hda_codec: invalid dep_range_val 0:7fff
[   23.572000] hda_codec: invalid dep_range_val 0:7fff
[   23.572000] hda_codec: invalid dep_range_val 0:7fff
[   23.572000] hda_codec: invalid dep_range_val 0:7fff
[   23.572000] hda_codec: invalid dep_range_val 0:7fff
[   23.572000] hda_codec: invalid dep_range_val 0:7fff
[   23.572000] hda_codec: invalid dep_range_val 0:7fff
[   23.572000] hda_codec: invalid dep_range_val 0:7fff
[   23.572000] hda_codec: invalid dep_range_val 0:7fff
[   23.572000] hda_codec: invalid dep_range_val 0:7fff
[   23.572000] hda_codec: invalid dep_range_val 0:7fff
[   23.572000] hda_codec: invalid dep_range_val 0:7fff
[   23.572000] hda_codec: invalid dep_range_val 0:7fff
[   23.572000] hda_codec: invalid dep_range_val 0:7fff
[   23.572000] hda_codec: invalid dep_range_val 0:7fff
[   23.572000] hda_codec: invalid dep_range_val 0:7fff
[   23.572000] hda_codec: invalid dep_range_val 0:7fff
[   23.572000] hda_codec: invalid dep_range_val 0:7fff
[   23.572000] hda_codec: invalid dep_range_val 0:7fff
[   23.572000] hda_codec: invalid dep_range_val 0:7fff
[   23.572000] hda_codec: invalid dep_range_val 0:7fff
[   23.572000] hda_codec: invalid dep_range_val 0:7fff
[   23.572000] hda_codec: invalid dep_range_val 0:7fff
[   23.572000] hda_codec: invalid dep_range_val 0:7fff
[   23.572000] hda_codec: invalid dep_range_val 0:7fff
[   23.572000] hda_codec: invalid dep_range_val 0:7fff
[   23.572000] hda_codec: invalid dep_range_val 0:7fff
[   23.572000] hda_codec: invalid dep_range_val 0:7fff
[   23.572000] hda_codec: invalid dep_range_val 0:7fff
[   23.572000] hda_codec: invalid dep_range_val 0:7fff
[   23.576000] hda_codec: invalid dep_range_val 0:7fff
[   23.576000] hda_codec: invalid dep_range_val 0:7fff
[   23.576000] hda_codec: invalid dep_range_val 0:7fff
[   23.576000] hda_codec: invalid dep_range_val 0:7fff
[   23.576000] hda_codec: invalid dep_range_val 0:7fff
[   23.576000] hda_codec: invalid dep_range_val 0:7fff
[   23.576000] hda_codec: invalid dep_range_val 0:7fff
[   23.576000] hda_codec: invalid dep_range_val 0:7fff
[   23.576000] hda_codec: invalid dep_range_val 0:7fff
[   23.576000] hda_codec: invalid dep_range_val 0:7fff
[   23.576000] hda_codec: invalid dep_range_val 0:7fff
[   23.576000] hda_codec: invalid dep_range_val 0:7fff
[   23.576000] hda_codec: invalid dep_range_val 0:7fff
[   23.576000] hda_codec: invalid dep_range_val 0:7fff
[   23.576000] hda_codec: invalid dep_range_val 0:7fff
[   23.576000] hda_codec: invalid dep_range_val 0:7fff
[   23.576000] hda_codec: invalid dep_range_val 0:7fff
[   23.576000] hda_codec: invalid dep_range_val 0:7fff
[   23.576000] hda_codec: invalid dep_range_val 0:7fff
[   23.576000] hda_codec: invalid dep_range_val 0:7fff
[   23.576000] hda_codec: invalid dep_range_val 0:7fff
[   23.576000] hda_codec: invalid dep_range_val 0:7fff
[   23.576000] hda_codec: invalid dep_range_val 0:7fff
[   23.576000] hda_codec: invalid dep_range_val 0:7fff
[   23.576000] hda_codec: invalid dep_range_val 0:7fff
[   23.576000] hda_codec: invalid dep_range_val 0:7fff
[   23.576000] hda_codec: invalid dep_range_val 0:7fff
[   23.576000] hda_codec: invalid dep_range_val 0:7fff
[   23.576000] hda_codec: invalid dep_range_val 0:7fff
[   23.576000] hda_codec: invalid dep_range_val 0:7fff
[   23.576000] hda_codec: invalid dep_range_val 0:7fff
[   23.576000] hda_codec: invalid dep_range_val 0:7fff
[   23.576000] hda_codec: invalid dep_range_val 0:7fff
[   23.576000] hda_codec: invalid dep_range_val 0:7fff
[   23.576000] hda_codec: invalid dep_range_val 0:7fff
[   23.576000] hda_codec: invalid dep_range_val 0:7fff
[   23.576000] hda_codec: invalid dep_range_val 0:7fff
[   23.576000] hda_codec: invalid dep_range_val 0:7fff
[   23.576000] hda_codec: invalid dep_range_val 0:7fff
[   23.576000] hda_codec: invalid dep_range_val 0:7fff
[   23.576000] hda_codec: invalid dep_range_val 0:7fff
[   23.576000] hda_codec: invalid dep_range_val 0:7fff
[   23.576000] hda_codec: invalid dep_range_val 0:7fff
[   23.576000] hda_codec: invalid dep_range_val 0:7fff
[   23.576000] hda_codec: invalid dep_range_val 0:7fff
[   23.576000] hda_codec: invalid dep_range_val 0:7fff
[   23.576000] hda_codec: invalid dep_range_val 0:7fff
[   23.576000] hda_codec: invalid dep_range_val 0:7fff
[   23.576000] hda_codec: invalid dep_range_val 0:7fff
[   23.576000] hda_codec: invalid dep_range_val 0:7fff
[   23.576000] hda_codec: invalid dep_range_val 0:7fff
[   23.576000] hda_codec: invalid dep_range_val 0:7fff
[   23.576000] hda_codec: invalid dep_range_val 0:7fff
[   23.576000] hda_codec: invalid dep_range_val 0:7fff
[   23.576000] hda_codec: invalid dep_range_val 0:7fff
[   23.576000] hda_codec: invalid dep_range_val 0:7fff
[   23.576000] hda_codec: invalid dep_range_val 0:7fff
[   23.576000] hda_codec: invalid dep_range_val 0:7fff
[   23.576000] hda_codec: invalid dep_range_val 0:7fff
[   23.576000] hda_codec: invalid dep_range_val 0:7fff
[   23.576000] hda_codec: invalid dep_range_val 0:7fff
[   23.576000] hda_codec: invalid dep_range_val 0:7fff
[   23.576000] hda_codec: invalid dep_range_val 0:7fff
[   23.576000] hda_codec: invalid dep_range_val 0:7fff
[   23.576000] hda_codec: invalid dep_range_val 0:7fff
[   23.576000] hda_codec: invalid dep_range_val 0:7fff
[   23.576000] hda_codec: invalid dep_range_val 0:7fff
[   23.576000] hda_codec: invalid dep_range_val 0:7fff
[   23.576000] hda_codec: invalid dep_range_val 0:7fff
[   23.576000] hda_codec: invalid dep_range_val 0:7fff
[   23.576000] hda_codec: invalid dep_range_val 0:7fff
[   23.580000] hda_codec: invalid dep_range_val 0:7fff
[   23.580000] hda_codec: invalid dep_range_val 0:7fff
[   23.580000] hda_codec: invalid dep_range_val 0:7fff
[   23.580000] hda_codec: invalid dep_range_val 0:7fff
[   23.580000] hda_codec: invalid dep_range_val 0:7fff
[   23.580000] hda_codec: invalid dep_range_val 0:7fff
[   23.580000] hda_codec: invalid dep_range_val 0:7fff
[   23.580000] hda_codec: invalid dep_range_val 0:7fff
[   23.580000] hda_codec: invalid dep_range_val 0:7fff
[   23.580000] hda_codec: invalid dep_range_val 0:7fff
[   23.580000] hda_codec: invalid dep_range_val 0:7fff
[   23.580000] hda_codec: invalid dep_range_val 0:7fff
[   23.580000] hda_codec: invalid dep_range_val 0:7fff
[   23.580000] hda_codec: invalid dep_range_val 0:7fff
[   23.580000] hda_codec: invalid dep_range_val 0:7fff
[   23.580000] hda_codec: invalid dep_range_val 0:7fff
[   23.580000] hda_codec: invalid dep_range_val 0:7fff
[   23.580000] hda_codec: invalid dep_range_val 0:7fff
[   23.580000] hda_codec: invalid dep_range_val 0:7fff
[   23.580000] hda_codec: invalid dep_range_val 0:7fff
[   23.580000] hda_codec: invalid dep_range_val 0:7fff
[   23.580000] hda_codec: invalid dep_range_val 0:7fff
[   23.580000] hda_codec: invalid dep_range_val 0:7fff
[   23.580000] hda_codec: invalid dep_range_val 0:7fff
[   23.580000] hda_codec: invalid dep_range_val 0:7fff
[   23.580000] hda_codec: invalid dep_range_val 0:7fff
[   23.580000] hda_codec: invalid dep_range_val 0:7fff
[   23.580000] hda_codec: invalid dep_range_val 0:7fff
[   23.580000] hda_codec: invalid dep_range_val 0:7fff
[   23.580000] hda_codec: invalid dep_range_val 0:7fff
[   23.580000] hda_codec: invalid dep_range_val 0:7fff
[   23.580000] hda_codec: invalid dep_range_val 0:7fff
[   23.580000] hda_codec: invalid dep_range_val 0:7fff
[   23.580000] hda_codec: invalid dep_range_val 0:7fff
[   23.580000] hda_codec: invalid dep_range_val 0:7fff
[   23.580000] hda_codec: invalid dep_range_val 0:7fff
[   23.580000] hda_codec: invalid dep_range_val 0:7fff
[   23.580000] hda_codec: invalid dep_range_val 0:7fff
[   23.580000] hda_codec: invalid dep_range_val 0:7fff
[   23.580000] hda_codec: invalid dep_range_val 0:7fff
[   23.580000] hda_codec: invalid dep_range_val 0:7fff
[   23.580000] hda_codec: invalid dep_range_val 0:7fff
[   23.580000] hda_codec: invalid dep_range_val 0:7fff
[   23.580000] hda_codec: invalid dep_range_val 0:7fff
[   23.580000] hda_codec: invalid dep_range_val 0:7fff
[   23.580000] hda_codec: invalid dep_range_val 0:7fff
[   23.580000] hda_codec: invalid dep_range_val 0:7fff
[   23.580000] hda_codec: invalid dep_range_val 0:7fff
[   23.580000] hda_codec: invalid dep_range_val 0:7fff
[   23.580000] hda_codec: invalid dep_range_val 0:7fff
[   23.580000] hda_codec: invalid dep_range_val 0:7fff
[   23.580000] hda_codec: invalid dep_range_val 0:7fff
[   23.580000] hda_codec: invalid dep_range_val 0:7fff
[   23.580000] hda_codec: invalid dep_range_val 0:7fff
[   23.580000] hda_codec: invalid dep_range_val 0:7fff
[   23.580000] hda_codec: invalid dep_range_val 0:7fff
[   23.580000] hda_codec: invalid dep_range_val 0:7fff
[   23.580000] hda_codec: invalid dep_range_val 0:7fff
[   23.580000] hda_codec: invalid dep_range_val 0:7fff
[   23.580000] hda_codec: invalid dep_range_val 0:7fff
[   23.580000] hda_codec: invalid dep_range_val 0:7fff
[   23.580000] hda_codec: invalid dep_range_val 0:7fff
[   23.580000] hda_codec: invalid dep_range_val 0:7fff
[   23.580000] hda_codec: invalid dep_range_val 0:7fff
[   23.580000] hda_codec: invalid dep_range_val 0:7fff
[   23.580000] hda_codec: invalid dep_range_val 0:7fff
[   23.580000] hda_codec: invalid dep_range_val 0:7fff
[   23.580000] hda_codec: invalid dep_range_val 0:7fff
[   23.580000] hda_codec: invalid dep_range_val 0:7fff
[   23.580000] hda_codec: invalid dep_range_val 0:7fff
[   23.580000] hda_codec: invalid dep_range_val 0:7fff
[   23.580000] hda_codec: invalid dep_range_val 0:7fff
[   23.580000] hda_codec: invalid dep_range_val 0:7fff
[   23.580000] hda_codec: invalid dep_range_val 0:7fff
[   23.580000] hda_codec: invalid dep_range_val 0:7fff
[   23.580000] hda_codec: invalid dep_range_val 0:7fff
[   23.584000] hda_codec: invalid dep_range_val 0:7fff
[   23.584000] hda_codec: invalid dep_range_val 0:7fff
[   23.584000] hda_codec: invalid dep_range_val 0:7fff
[   23.584000] hda_codec: invalid dep_range_val 0:7fff
[   23.584000] hda_codec: invalid dep_range_val 0:7fff
[   23.584000] hda_codec: invalid dep_range_val 0:7fff
[   23.584000] hda_codec: invalid dep_range_val 0:7fff
[   23.584000] hda_codec: invalid dep_range_val 0:7fff
[   23.584000] hda_codec: invalid dep_range_val 0:7fff
[   23.584000] hda_codec: invalid dep_range_val 0:7fff
[   23.584000] hda_codec: invalid dep_range_val 0:7fff
[   23.584000] hda_codec: invalid dep_range_val 0:7fff
[   23.584000] hda_codec: invalid dep_range_val 0:7fff
[   23.584000] hda_codec: invalid dep_range_val 0:7fff
[   23.584000] hda_codec: invalid dep_range_val 0:7fff
[   23.584000] hda_codec: invalid dep_range_val 0:7fff
[   23.584000] hda_codec: invalid dep_range_val 0:7fff
[   23.584000] hda_codec: invalid dep_range_val 0:7fff
[   23.584000] hda_codec: invalid dep_range_val 0:7fff
[   23.584000] hda_codec: invalid dep_range_val 0:7fff
[   23.584000] hda_codec: invalid dep_range_val 0:7fff
[   23.584000] hda_codec: invalid dep_range_val 0:7fff
[   23.584000] hda_codec: invalid dep_range_val 0:7fff
[   23.584000] hda_codec: invalid dep_range_val 0:7fff
[   23.584000] hda_codec: invalid dep_range_val 0:7fff
[   23.584000] hda_codec: invalid dep_range_val 0:7fff
[   23.584000] hda_codec: invalid dep_range_val 0:7fff
[   23.584000] hda_codec: invalid dep_range_val 0:7fff
[   23.584000] hda_codec: invalid dep_range_val 0:7fff
[   23.584000] hda_codec: invalid dep_range_val 0:7fff
[   23.584000] hda_codec: invalid dep_range_val 0:7fff
[   23.584000] hda_codec: invalid dep_range_val 0:7fff
[   23.584000] hda_codec: invalid dep_range_val 0:7fff
[   23.584000] hda_codec: invalid dep_range_val 0:7fff
[   23.584000] hda_codec: invalid dep_range_val 0:7fff
[   23.584000] hda_codec: invalid dep_range_val 0:7fff
[   23.584000] hda_codec: invalid dep_range_val 0:7fff
[   23.584000] hda_codec: invalid dep_range_val 0:7fff
[   23.584000] hda_codec: invalid dep_range_val 0:7fff
[   23.584000] hda_codec: invalid dep_range_val 0:7fff
[   23.584000] hda_codec: invalid dep_range_val 0:7fff
[   23.584000] hda_codec: invalid dep_range_val 0:7fff
[   23.584000] hda_codec: invalid dep_range_val 0:7fff
[   23.584000] hda_codec: invalid dep_range_val 0:7fff
[   23.584000] hda_codec: invalid dep_range_val 0:7fff
[   23.584000] hda_codec: invalid dep_range_val 0:7fff
[   23.584000] hda_codec: invalid dep_range_val 0:7fff
[   23.584000] hda_codec: invalid dep_range_val 0:7fff
[   23.584000] hda_codec: invalid dep_range_val 0:7fff
[   23.584000] hda_codec: invalid dep_range_val 0:7fff
[   23.584000] hda_codec: invalid dep_range_val 0:7fff
[   23.584000] hda_codec: invalid dep_range_val 0:7fff
[   23.584000] hda_codec: invalid dep_range_val 0:7fff
[   23.584000] hda_codec: invalid dep_range_val 0:7fff
[   23.584000] hda_codec: invalid dep_range_val 0:7fff
[   23.584000] hda_codec: invalid dep_range_val 0:7fff
[   23.584000] hda_codec: invalid dep_range_val 0:7fff
[   23.584000] hda_codec: invalid dep_range_val 0:7fff
[   23.584000] hda_codec: invalid dep_range_val 0:7fff
[   23.584000] hda_codec: invalid dep_range_val 0:7fff
[   23.584000] hda_codec: invalid dep_range_val 0:7fff
[   23.584000] hda_codec: invalid dep_range_val 0:7fff
[   23.584000] hda_codec: invalid dep_range_val 0:7fff
[   23.584000] hda_codec: invalid dep_range_val 0:7fff
[   23.584000] hda_codec: invalid dep_range_val 0:7fff
[   23.584000] hda_codec: invalid dep_range_val 0:7fff
[   23.584000] hda_codec: invalid dep_range_val 0:7fff
[   23.584000] hda_codec: invalid dep_range_val 0:7fff
[   23.584000] hda_codec: invalid dep_range_val 0:7fff
[   23.584000] hda_codec: invalid dep_range_val 0:7fff
[   23.584000] hda_codec: invalid dep_range_val 0:7fff
[   23.588000] hda_codec: invalid dep_range_val 0:7fff
[   23.588000] hda_codec: invalid dep_range_val 0:7fff
[   23.588000] hda_codec: invalid dep_range_val 0:7fff
[   23.588000] hda_codec: invalid dep_range_val 0:7fff
[   23.588000] hda_codec: invalid dep_range_val 0:7fff
[   23.588000] hda_codec: invalid dep_range_val 0:7fff
[   23.588000] hda_codec: invalid dep_range_val 0:7fff
[   23.588000] hda_codec: invalid dep_range_val 0:7fff
[   23.588000] hda_codec: invalid dep_range_val 0:7fff
[   23.588000] hda_codec: invalid dep_range_val 0:7fff
[   23.588000] hda_codec: invalid dep_range_val 0:7fff
[   23.588000] hda_codec: invalid dep_range_val 0:7fff
[   23.588000] hda_codec: invalid dep_range_val 0:7fff
[   23.588000] hda_codec: invalid dep_range_val 0:7fff
[   23.588000] hda_codec: invalid dep_range_val 0:7fff
[   23.588000] hda_codec: invalid dep_range_val 0:7fff
[   23.588000] hda_codec: invalid dep_range_val 0:7fff
[   23.588000] hda_codec: invalid dep_range_val 0:7fff
[   23.588000] hda_codec: invalid dep_range_val 0:7fff
[   23.588000] hda_codec: invalid dep_range_val 0:7fff
[   23.588000] hda_codec: invalid dep_range_val 0:7fff
[   23.588000] hda_codec: invalid dep_range_val 0:7fff
[   23.588000] hda_codec: invalid dep_range_val 0:7fff
[   23.588000] hda_codec: invalid dep_range_val 0:7fff
[   23.588000] hda_codec: invalid dep_range_val 0:7fff
[   23.588000] hda_codec: invalid dep_range_val 0:7fff
[   23.588000] hda_codec: invalid dep_range_val 0:7fff
[   23.588000] hda_codec: invalid dep_range_val 0:7fff
[   23.588000] hda_codec: invalid dep_range_val 0:7fff
[   23.588000] hda_codec: invalid dep_range_val 0:7fff
[   23.588000] hda_codec: invalid dep_range_val 0:7fff
[   23.588000] hda_codec: invalid dep_range_val 0:7fff
[   23.588000] hda_codec: invalid dep_range_val 0:7fff
[   23.588000] hda_codec: invalid dep_range_val 0:7fff
[   23.588000] hda_codec: invalid dep_range_val 0:7fff
[   23.588000] hda_codec: invalid dep_range_val 0:7fff
[   23.588000] hda_codec: invalid dep_range_val 0:7fff
[   23.588000] hda_codec: invalid dep_range_val 0:7fff
[   23.588000] hda_codec: invalid dep_range_val 0:7fff
[   23.588000] hda_codec: invalid dep_range_val 0:7fff
[   23.588000] hda_codec: invalid dep_range_val 0:7fff
[   23.588000] hda_codec: invalid dep_range_val 0:7fff
[   23.588000] hda_codec: invalid dep_range_val 0:7fff
[   23.588000] hda_codec: invalid dep_range_val 0:7fff
[   23.588000] hda_codec: invalid dep_range_val 0:7fff
[   23.588000] hda_codec: invalid dep_range_val 0:7fff
[   23.588000] hda_codec: invalid dep_range_val 0:7fff
[   23.588000] hda_codec: invalid dep_range_val 0:7fff
[   23.588000] hda_codec: invalid dep_range_val 0:7fff
[   23.588000] hda_codec: invalid dep_range_val 0:7fff
[   23.588000] hda_codec: invalid dep_range_val 0:7fff
[   23.588000] hda_codec: invalid dep_range_val 0:7fff
[   23.588000] hda_codec: invalid dep_range_val 0:7fff
[   23.588000] hda_codec: invalid dep_range_val 0:7fff
[   23.588000] hda_codec: invalid dep_range_val 0:7fff
[   23.588000] hda_codec: invalid dep_range_val 0:7fff
[   23.588000] hda_codec: invalid dep_range_val 0:7fff
[   23.588000] hda_codec: invalid dep_range_val 0:7fff
[   23.588000] hda_codec: invalid dep_range_val 0:7fff
[   23.588000] hda_codec: invalid dep_range_val 0:7fff
[   23.588000] hda_codec: invalid dep_range_val 0:7fff
[   23.588000] hda_codec: invalid dep_range_val 0:7fff
[   23.588000] hda_codec: invalid dep_range_val 0:7fff
[   23.588000] hda_codec: invalid dep_range_val 0:7fff
[   23.588000] hda_codec: invalid dep_range_val 0:7fff
[   23.588000] hda_codec: invalid dep_range_val 0:7fff
[   23.588000] hda_codec: invalid dep_range_val 0:7fff
[   23.588000] hda_codec: invalid dep_range_val 0:7fff
[   23.588000] hda_codec: invalid dep_range_val 0:7fff
[   23.588000] hda_codec: invalid dep_range_val 0:7fff
[   23.588000] hda_codec: invalid dep_range_val 0:7fff
[   23.588000] hda_codec: invalid dep_range_val 0:7fff
[   23.588000] hda_codec: invalid dep_range_val 0:7fff
[   23.588000] hda_codec: invalid dep_range_val 0:7fff
[   23.588000] hda_codec: invalid dep_range_val 0:7fff
[   23.588000] hda_codec: invalid dep_range_val 0:7fff
[   23.588000] hda_codec: invalid dep_range_val 0:7fff
[   23.588000] hda_codec: invalid dep_range_val 0:7fff
[   23.592000] hda_codec: invalid dep_range_val 0:7fff
[   23.592000] hda_codec: invalid dep_range_val 0:7fff
[   23.592000] hda_codec: invalid dep_range_val 0:7fff
[   23.592000] hda_codec: invalid dep_range_val 0:7fff
[   23.592000] hda_codec: invalid dep_range_val 0:7fff
[   23.592000] hda_codec: invalid dep_range_val 0:7fff
[   23.592000] hda_codec: invalid dep_range_val 0:7fff
[   23.592000] hda_codec: invalid dep_range_val 0:7fff
[   23.592000] hda_codec: invalid dep_range_val 0:7fff
[   23.592000] hda_codec: invalid dep_range_val 0:7fff
[   23.592000] hda_codec: invalid dep_range_val 0:7fff
[   23.592000] hda_codec: invalid dep_range_val 0:7fff
[   23.592000] hda_codec: invalid dep_range_val 0:7fff
[   23.592000] hda_codec: invalid dep_range_val 0:7fff
[   23.592000] hda_codec: invalid dep_range_val 0:7fff
[   23.592000] hda_codec: invalid dep_range_val 0:7fff
[   23.592000] hda_codec: invalid dep_range_val 0:7fff
[   23.592000] hda_codec: invalid dep_range_val 0:7fff
[   23.592000] hda_codec: invalid dep_range_val 0:7fff
[   23.592000] hda_codec: invalid dep_range_val 0:7fff
[   23.592000] hda_codec: invalid dep_range_val 0:7fff
[   23.592000] hda_codec: invalid dep_range_val 0:7fff
[   23.592000] hda_codec: invalid dep_range_val 0:7fff
[   23.592000] hda_codec: invalid dep_range_val 0:7fff
[   23.592000] hda_codec: invalid dep_range_val 0:7fff
[   23.592000] hda_codec: invalid dep_range_val 0:7fff
[   23.592000] hda_codec: invalid dep_range_val 0:7fff
[   23.592000] hda_codec: invalid dep_range_val 0:7fff
[   23.592000] hda_codec: invalid dep_range_val 0:7fff
[   23.764000] fuse init (API version 7.8)
[   23.780000] hda_codec: num_steps = 0 for NID=0xd
[   23.780000] hda_codec: num_steps = 0 for NID=0xd
[   23.784000] hda_codec: num_steps = 0 for NID=0xd
[   23.788000] hda_codec: num_steps = 0 for NID=0x18
[   23.788000] hda_codec: num_steps = 0 for NID=0x19
[   23.788000] hda_codec: num_steps = 0 for NID=0x9
[   23.816000] hda_codec: num_steps = 0 for NID=0x19
[   23.820000] hda_codec: num_steps = 0 for NID=0x19
[   23.824000] hda_codec: num_steps = 0 for NID=0x19
[   23.828000] hda_codec: num_steps = 0 for NID=0x19
[   23.832000] hda_codec: num_steps = 0 for NID=0x19
[   23.832000] hda_codec: num_steps = 0 for NID=0x19
[   23.836000] hda_codec: num_steps = 0 for NID=0x19
[   23.840000] hda_codec: num_steps = 0 for NID=0x19
[   23.844000] hda_codec: num_steps = 0 for NID=0x19
[   23.848000] hda_codec: num_steps = 0 for NID=0x19
[   23.852000] hda_codec: num_steps = 0 for NID=0x19
[   23.856000] hda_codec: num_steps = 0 for NID=0x19
[   23.860000] hda_codec: num_steps = 0 for NID=0x19
[   23.864000] hda_codec: num_steps = 0 for NID=0x19
[   23.868000] hda_codec: num_steps = 0 for NID=0x19
[   23.872000] hda_codec: num_steps = 0 for NID=0x19
[   23.876000] hda_codec: num_steps = 0 for NID=0x19
[   23.880000] hda_codec: num_steps = 0 for NID=0x19
[   23.884000] hda_codec: num_steps = 0 for NID=0x19
[   23.888000] hda_codec: num_steps = 0 for NID=0x19
[   23.892000] hda_codec: num_steps = 0 for NID=0x19
[   23.896000] hda_codec: num_steps = 0 for NID=0x19
[   23.900000] hda_codec: num_steps = 0 for NID=0x19
[   23.904000] hda_codec: num_steps = 0 for NID=0x19
[   23.908000] hda_codec: num_steps = 0 for NID=0x19
[   23.912000] hda_codec: num_steps = 0 for NID=0x19
[   23.916000] hda_codec: num_steps = 0 for NID=0x19
[   23.920000] hda_codec: num_steps = 0 for NID=0x19
[   23.924000] hda_codec: num_steps = 0 for NID=0x19
[   23.928000] hda_codec: num_steps = 0 for NID=0x19
[   23.932000] hda_codec: num_steps = 0 for NID=0x19
[   23.936000] hda_codec: num_steps = 0 for NID=0x19
[   23.940000] hda_codec: num_steps = 0 for NID=0xd
[   23.940000] hda_codec: num_steps = 0 for NID=0xd
[   23.944000] hda_codec: num_steps = 0 for NID=0xd
[   23.944000] hda_codec: num_steps = 0 for NID=0x18
[   23.944000] hda_codec: num_steps = 0 for NID=0x19
[   23.944000] hda_codec: num_steps = 0 for NID=0x9
[   23.960000] lp: driver loaded but no devices found
[   23.984000] Adding 1076344k swap on /dev/disk/by-uuid/e163e51f-3f93-4c96-beab-844c9c572eb7.  Priority:-1 extents:1 across:1076344k
[   24.120000] EXT3 FS on hda1, internal journal
[   24.384000] NET: Registered protocol family 10
[   24.384000] lo: Disabled Privacy Extensions
[   24.444000] kjournald starting.  Commit interval 5 seconds
[   24.444000] EXT3 FS on hda3, internal journal
[   24.444000] EXT3-fs: mounted filesystem with ordered data mode.
[   29.936000] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
[   29.940000] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
[   29.952000] Using specific hotkey driver
[   30.088000] ACPI: Battery Slot [BAT1] (battery present)
[   30.120000] ibm_acpi: ec object not found
[   30.176000] No dock devices found.
[   30.220000] input: Power Button (FF) as /class/input/input4
[   30.224000] ACPI: Power Button (FF) [PWRF]
[   30.256000] input: Lid Switch as /class/input/input5
[   30.260000] ACPI: Lid Switch [LID]
[   30.296000] input: Power Button (CM) as /class/input/input6
[   30.296000] ACPI: Power Button (CM) [PWRB]
[   30.332000] input: Sleep Button (CM) as /class/input/input7
[   30.336000] ACPI: Sleep Button (CM) [SLPB]
[   30.368000] ACPI: AC Adapter [ACAD] (on-line)
[   30.460000] pcc_acpi: loading...
[   30.464000] wmi_add device=da07a000
[   30.464000] calling WQBA
[   30.656000] powernow-k8: Found 1 AMD Turion(tm) 64 Mobile Technology MK-36 processors (version 2.00.00)
[   30.656000] powernow-k8:    0 : fid 0xc (2000 MHz), vid 0x10
[   30.656000] powernow-k8:    1 : fid 0xa (1800 MHz), vid 0x12
[   30.656000] powernow-k8:    2 : fid 0x8 (1600 MHz), vid 0x14
[   30.656000] powernow-k8:    3 : fid 0x0 (800 MHz), vid 0x18
[   36.508000] ppdev: user-space parallel port driver
[   37.236000] apm: BIOS not found.
[   37.424000] Bluetooth: Core ver 2.11
[   37.424000] NET: Registered protocol family 31
[   37.424000] Bluetooth: HCI device and connection manager initialized
[   37.424000] Bluetooth: HCI socket layer initialized
[   37.464000] Bluetooth: L2CAP ver 2.8
[   37.464000] Bluetooth: L2CAP socket layer initialized
[   37.612000] Bluetooth: RFCOMM socket layer initialized
[   37.612000] Bluetooth: RFCOMM TTY layer initialized
[   37.612000] Bluetooth: RFCOMM ver 1.8
[   40.256000] hda-intel: Invalid position buffer, using LPIB read method instead.
[   48.664000] eth0: no IPv6 routers present
[   53.608000] hda_codec: num_steps = 0 for NID=0x19
[   64.916000] hda_codec: num_steps = 0 for NID=0x19
[  124.764000] usb 3-1: new high speed USB device using ehci_hcd and address 2
[  124.820000] ehci_hcd 0000:00:13.2: port 1 reset error -110
[  124.820000] hub 3-0:1.0: hub_port_status failed (err = -32)
[  125.024000] ehci_hcd 0000:00:13.2: port 1 reset error -110
[  125.024000] hub 3-0:1.0: hub_port_status failed (err = -32)
[  125.228000] ehci_hcd 0000:00:13.2: port 1 reset error -110
[  125.228000] hub 3-0:1.0: hub_port_status failed (err = -32)
[  125.432000] ehci_hcd 0000:00:13.2: port 1 reset error -110
[  125.432000] hub 3-0:1.0: hub_port_status failed (err = -32)
[  125.636000] ehci_hcd 0000:00:13.2: port 1 reset error -110
[  125.636000] hub 3-0:1.0: hub_port_status failed (err = -32)
[  125.636000] hub 3-0:1.0: Cannot enable port 1.  Maybe the USB cable is bad?
[  125.692000] ehci_hcd 0000:00:13.2: port 1 reset error -110
[  125.692000] hub 3-0:1.0: hub_port_status failed (err = -32)
[  125.896000] ehci_hcd 0000:00:13.2: port 1 reset error -110
[  125.896000] hub 3-0:1.0: hub_port_status failed (err = -32)

```

---

### Post by shockingelk on 2007-08-13
When I plug in a PowerShot A540:

```
Aug 13 22:04:14 erik-laptop kernel: [ 2445.792000] usb 1-4: new full speed USB device using ohci_hcd and address 26
Aug 13 22:04:14 erik-laptop kernel: [ 2445.972000] usb 1-4: device descriptor read/64, error -62
Aug 13 22:04:15 erik-laptop kernel: [ 2446.256000] usb 1-4: device descriptor read/64, error -62
Aug 13 22:04:15 erik-laptop kernel: [ 2446.536000] usb 1-4: new full speed USB device using ohci_hcd and address 27
```

---

### Post by shockingelk on 2007-08-14
When plugging in a USB memory stick - any suggestions? I can't find any suggestions where to start when NO USB device works.

```
Aug 14 12:35:18 erik-laptop kernel: [ 1334.604000] usb 3-1: new high speed USB device using ehci_hcd and address 2
Aug 14 12:35:18 erik-laptop kernel: [ 1334.660000] ehci_hcd 0000:00:13.2: port 1 reset error -110
Aug 14 12:35:18 erik-laptop kernel: [ 1334.660000] hub 3-0:1.0: hub_port_status failed (err = -32)
Aug 14 12:35:18 erik-laptop kernel: [ 1334.864000] ehci_hcd 0000:00:13.2: port 1 reset error -110
Aug 14 12:35:18 erik-laptop kernel: [ 1334.864000] hub 3-0:1.0: hub_port_status failed (err = -32)
Aug 14 12:35:19 erik-laptop kernel: [ 1335.068000] ehci_hcd 0000:00:13.2: port 1 reset error -110
Aug 14 12:35:19 erik-laptop kernel: [ 1335.068000] hub 3-0:1.0: hub_port_status failed (err = -32)
Aug 14 12:35:19 erik-laptop kernel: [ 1335.272000] ehci_hcd 0000:00:13.2: port 1 reset error -110
Aug 14 12:35:19 erik-laptop kernel: [ 1335.272000] hub 3-0:1.0: hub_port_status failed (err = -32)
Aug 14 12:35:19 erik-laptop kernel: [ 1335.476000] ehci_hcd 0000:00:13.2: port 1 reset error -110
Aug 14 12:35:19 erik-laptop kernel: [ 1335.476000] hub 3-0:1.0: hub_port_status failed (err = -32)
Aug 14 12:35:19 erik-laptop kernel: [ 1335.476000] hub 3-0:1.0: Cannot enable port 1.  Maybe the USB cable is bad?
Aug 14 12:35:19 erik-laptop kernel: [ 1335.532000] ehci_hcd 0000:00:13.2: port 1 reset error -110
Aug 14 12:35:19 erik-laptop kernel: [ 1335.532000] hub 3-0:1.0: hub_port_status failed (err = -32)
Aug 14 12:35:19 erik-laptop kernel: [ 1335.736000] ehci_hcd 0000:00:13.2: port 1 reset error -110
Aug 14 12:35:19 erik-laptop kernel: [ 1335.736000] hub 3-0:1.0: hub_port_status failed (err = -32)
Aug 14 12:35:19 erik-laptop kernel: [ 1335.940000] ehci_hcd 0000:00:13.2: port 1 reset error -110
Aug 14 12:35:19 erik-laptop kernel: [ 1335.940000] hub 3-0:1.0: hub_port_status failed (err = -32)
Aug 14 12:35:20 erik-laptop kernel: [ 1336.144000] ehci_hcd 0000:00:13.2: port 1 reset error -110
Aug 14 12:35:20 erik-laptop kernel: [ 1336.144000] hub 3-0:1.0: hub_port_status failed (err = -32)
Aug 14 12:35:20 erik-laptop kernel: [ 1336.348000] ehci_hcd 0000:00:13.2: port 1 reset error -110
Aug 14 12:35:20 erik-laptop kernel: [ 1336.348000] hub 3-0:1.0: hub_port_status failed (err = -32)
Aug 14 12:35:20 erik-laptop kernel: [ 1336.348000] hub 3-0:1.0: Cannot enable port 1.  Maybe the USB cable is bad?
Aug 14 12:35:20 erik-laptop kernel: [ 1336.404000] ehci_hcd 0000:00:13.2: port 1 reset error -110
Aug 14 12:35:20 erik-laptop kernel: [ 1336.404000] hub 3-0:1.0: hub_port_status failed (err = -32)
Aug 14 12:35:20 erik-laptop kernel: [ 1336.608000] ehci_hcd 0000:00:13.2: port 1 reset error -110
Aug 14 12:35:20 erik-laptop kernel: [ 1336.608000] hub 3-0:1.0: hub_port_status failed (err = -32)
Aug 14 12:35:20 erik-laptop kernel: [ 1336.812000] ehci_hcd 0000:00:13.2: port 1 reset error -110
Aug 14 12:35:20 erik-laptop kernel: [ 1336.812000] hub 3-0:1.0: hub_port_status failed (err = -32)
Aug 14 12:35:20 erik-laptop kernel: [ 1337.016000] ehci_hcd 0000:00:13.2: port 1 reset error -110
Aug 14 12:35:20 erik-laptop kernel: [ 1337.016000] hub 3-0:1.0: hub_port_status failed (err = -32)
Aug 14 12:35:21 erik-laptop kernel: [ 1337.220000] ehci_hcd 0000:00:13.2: port 1 reset error -110
Aug 14 12:35:21 erik-laptop kernel: [ 1337.220000] hub 3-0:1.0: hub_port_status failed (err = -32)
Aug 14 12:35:21 erik-laptop kernel: [ 1337.220000] hub 3-0:1.0: Cannot enable port 1.  Maybe the USB cable is bad?
Aug 14 12:35:21 erik-laptop kernel: [ 1337.276000] ehci_hcd 0000:00:13.2: port 1 reset error -110
Aug 14 12:35:21 erik-laptop kernel: [ 1337.276000] hub 3-0:1.0: hub_port_status failed (err = -32)
Aug 14 12:35:21 erik-laptop kernel: [ 1337.480000] ehci_hcd 0000:00:13.2: port 1 reset error -110
Aug 14 12:35:21 erik-laptop kernel: [ 1337.480000] hub 3-0:1.0: hub_port_status failed (err = -32)
Aug 14 12:35:21 erik-laptop kernel: [ 1337.684000] ehci_hcd 0000:00:13.2: port 1 reset error -110
Aug 14 12:35:21 erik-laptop kernel: [ 1337.684000] hub 3-0:1.0: hub_port_status failed (err = -32)
Aug 14 12:35:21 erik-laptop kernel: [ 1337.888000] ehci_hcd 0000:00:13.2: port 1 reset error -110
Aug 14 12:35:21 erik-laptop kernel: [ 1337.888000] hub 3-0:1.0: hub_port_status failed (err = -32)
Aug 14 12:35:22 erik-laptop kernel: [ 1338.092000] ehci_hcd 0000:00:13.2: port 1 reset error -110
Aug 14 12:35:22 erik-laptop kernel: [ 1338.092000] hub 3-0:1.0: hub_port_status failed (err = -32)
Aug 14 12:35:22 erik-laptop kernel: [ 1338.092000] hub 3-0:1.0: Cannot enable port 1.  Maybe the USB cable is bad?
```

---

