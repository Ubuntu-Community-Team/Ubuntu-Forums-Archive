---
title: "Roll back update of gcc 4.3"
date: 2009-01-03
forum: Installation &amp; Upgrades
---

### Post by abel_bcn on 2009-01-03
I've upgraded my 2 pc's to intrepid, and on both upgrades my previous version of the g++ compiler was overwritten by the new 4.3.

I need it working so I want to go back to the previous version and I'm not really sure how to. I tried with Synaptic but couldn't find a way to replace my current release with the previous one.

Can someone guide me?

Thanks!

---

### Post by zvacet on 2009-01-03
```
sudo aptitude forbid-version filename
```

or for better understanding what are you doing type **man aptitude**.

---

### Post by abel_bcn on 2009-01-04
I still can't get it to work.

I've tried downloading another version through synaptic and forcing it over the new one but it won't find any other version.

Can I overwrite the files manually by downloading another release? If so, in which directory?

Thanks for your help.

---

