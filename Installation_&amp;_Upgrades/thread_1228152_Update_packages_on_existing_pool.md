---
title: "Update packages on existing pool"
date: 2009-07-31
forum: Installation &amp; Upgrades
---

### Post by bedge on 2009-07-31
Is there a tool to update the packages on an existing pool?

I have the unpacked install CD, but all the packages are out of date.

I can easily generate a list of packages in that pool, 

```
find cd-image/pool/main cd-image/pool/restricted -name \*.deb  | sed -e "s,.\+/\([^/_]\+\)_.\+,\1," | tr '\n' ' '
```

Is there anything that I can feed that list to in order to download the current versions and replace the contents of the pool?

---

