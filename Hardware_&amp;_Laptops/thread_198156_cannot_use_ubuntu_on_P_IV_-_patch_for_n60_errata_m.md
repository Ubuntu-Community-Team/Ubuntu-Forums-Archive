---
title: "cannot use ubuntu on P IV - patch for n60 errata makes it unusable"
date: 2006-06-16
forum: Hardware &amp; Laptops
---

### Post by Spiderdba on 2006-06-16
I have been using ubuntu on my laptop since 4.10, but in Breezy they introduced a kernel patch that doesn't let my cpu go below 2 Ghz. They introduced this patch because of a bug on P IV (N60 errata) that affects some pc... the problem is that my laptop is not affected from this bug and neverthless  is recognized as having it!!!! The only way to use Ubuntu was to compile a Vanilla Kernel... and then forget about having an updated system because it was very difficult to maintain it. Now with Dapper it's still the same situation! Not only battery lasts much less, but cpu fan is always on making a lot of noise and consuming a lot too.... and after 2 hours working it gets really hot!

I think is really a shame that developers cannot find a way to discern which cpu has the n60 errata and which not! At least they should provide a p4-clockmod module without the patch.

I have seen some posts on the argument, but still I cannot find a definitive solution to a problem that I think affects a lot of people.

There are some people who compiled a kernel just for this... but it needs to be updated too!!!!

It's incredible also that the only distribution that has this "feature" is [k-x-]ubuntu... I have tried a lot of them!

So.... can some developer discuss about it??

---

### Post by nomats on 2006-08-17
i suffer from this too. i often just irc or do something else as productive that doesn't require much processing power. still my cpu is constantly running at 2.1GHz. i think this should be corrected as soon as possible. and sure i could compile my own kernel, but then i'd be using gentoo, not ubuntu.

---

