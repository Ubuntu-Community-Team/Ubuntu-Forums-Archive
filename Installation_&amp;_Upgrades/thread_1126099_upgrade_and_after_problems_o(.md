---
title: "upgrade and after problems :o("
date: 2009-04-15
forum: Installation &amp; Upgrades
---

### Post by miroslav_karpis on 2009-04-15
hi all,
pls. can you help me with this...?

yesterday was everything working OK.

Today I was notified about a new nvidia driver - so I installed it and after a restart I got some error messages. PC was able to run in a 'safe' mode. SO I moved back to the old driver. Screen, etc..looked OK,...but now I'm getting following problem:

when I want to compile some of my programming I'm getting following:

/usr/bin/ld: cannot find -lGL
collect2: ld returned 1 exit status

](*,)

point is that if I go to /usr/bin there is no ld directory
I have checked some packages and all lookes installed (I'm not pro)

pls. any ideas?

---

### Post by miroslav_karpis on 2009-04-15
ok,...fixed it. I guess some NVIDIA, or installer bug?

fix:
the link in /usr/lib/ was broken for ligGL.so
so I needed to remake it:

```
sudo ln -sf /usr/lib/libGL.so.177.82 /usr/lib/libGL.so
```


libGL.so.177.82 of yours can be different - so just check it in the same fodler. In case it is different just change the name

---

