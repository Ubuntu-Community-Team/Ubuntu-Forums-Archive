---
title: "Dual screen flicker after suspend in 11.10"
date: 2011-10-25
forum: Hardware
---

### Post by audwan on 2011-10-25
I have a Dell Latitude laptop with a Benq 24" LCD attached via HDMI, and experience screen flickering occasionally on the second monitor.

It seems to happen after I suspend the computer with the monitor attached, resume without the screen, suspend and then start the computer with the monitor attached again. It usually takes a few tries of disabling/enabling the 24" before it responds, and when it does the image flickers horribly.

By the way I always disable the monitor in Ubuntu before I suspend it (lesson learned in previous versions of Ubuntu). The flickering was not there in 11.04.

Any tips would be appreciated.

---

### Post by audwan on 2011-11-01
I may have fixed it myself by resetting Compiz:

```

rm -rf .gconf/apps/compiz*
rm -rf .cache/compizconfig-1/
rm -rf .config/compiz-1/
rm -rf .compiz*

```

I'll check again a few times and report back.

EDIT: Yup. Tested multiple times and now it works great.

---

