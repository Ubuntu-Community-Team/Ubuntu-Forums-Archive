---
title: "oss in xubuntu"
date: 2007-12-08
forum: Hardware &amp; Laptops
---

### Post by Randy R on 2007-12-08
I have a very old notebook computer (dell inspiron 3500) running xubuntu (7.04) that uses a neomagic av256 sound card. As far as I can tell alsa will not work with this card. OSS 3.99 supports the card and when i run osstest, i get sound but that is the only sound I can get. No other applications get sound. OSS 4 and greater I am informed will not work with this card either. Am I out of luck?

I know this is kind of obscure but  any help at all would be appreciated.

Randy

If this is not the correct location for this post, please let me know where it should go

---

### Post by christhemonkey on 2007-12-08
Your card should work with ALSA with the module snd-nm256.

Please provide the output of this command:
```
lsmod | grep snd 
```

---

### Post by Randy R on 2007-12-08
There is no output from:

lsmod | grep snd

I have oss installed by the way. I believe that oss disables alsa. I can uninstall and reenable if it will work.

---

### Post by Randy R on 2008-02-06
I have given up on this. I went to an old sb8 alsa driver and that works.

---

