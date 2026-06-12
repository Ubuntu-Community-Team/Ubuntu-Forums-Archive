---
title: "Japanese input problem: Anthy won't convert kana to kanji"
date: 2008-07-20
forum: General Help
---

### Post by nielsk on 2008-07-20
Hi!


When I try using Anthy the kana-input works but I can't convert to kanji. It doesn't even recognize complete words. E.g. I type &#12431;&#12383;&#12375; and it offers me to convert each syllable to it's katakana-version but not to the kanji &#31169;. Same for anything else.

Canna and PRIME are working fine though. Using Canna now for some weeks I find it not as good as Anthy and I just tested PRIME and find it really strange to use. I tried my luck with Scim and UIM and I have with both the same problem. When I open the Dictionary Editor from UIM the dictionary of Anthy is empty but I'm not sure that's normal because I never used UIM before (maybe it's just newly added words?).

Right now I am using eeeXubuntu which is based on Xubuntu 7.10, all packages are up-to-date.

Does anyone has an idea what the problem could be?

---

### Post by nielsk on 2008-07-20
I tried update /var/lib/anthy.dic according to the instructions found [http://d.hatena.ne.jp/nshttsk/20070201/1170352330](http://d.hatena.ne.jp/nshttsk/20070201/1170352330) and [http://h2np.net/tips/anthy-diclist.html](http://h2np.net/tips/anthy-diclist.html) but it didn't help :(

anthy.dic's file size is still 4 byte.

---

### Post by vadarfone on 2008-07-25
Just an idea...

Have you looked in the setup of SCIM and selected Multisegment in the Conversion mode dialog?

Sorry if you already know this!

---

### Post by nielsk on 2008-07-25
Thx for that. But in that case it should have converted single syllables at least, shouldn't it? E.g. &#12376; as &#26178; or &#33258;

Btw. I did in the meantime I clean install of Ubuntu 8.04 and everything works OoB w/out any problems.

---

