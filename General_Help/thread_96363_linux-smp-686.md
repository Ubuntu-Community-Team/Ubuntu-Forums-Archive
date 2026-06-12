---
title: "linux-smp-686"
date: 2005-11-28
forum: General Help
---

### Post by etlatino on 2005-11-28
after installing linux-smp-686, my bootup screen comes up as kubuntu?

any reason? how to fix it?

Originally, I installed ubuntu and just to test out kde I installed the kubuntu desktop also.

---

### Post by Sutekh on 2005-11-28
Type this at a command line 
```

sudo update-alternatives --config usplash-artwork.so

```

This will list the possible splash screens, just enter the number of the one you wish to use and you're set.

---

