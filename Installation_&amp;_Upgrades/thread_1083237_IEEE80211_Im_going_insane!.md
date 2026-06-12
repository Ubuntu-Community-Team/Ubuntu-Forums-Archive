---
title: "IEEE80211 Im going insane!"
date: 2009-02-28
forum: Installation &amp; Upgrades
---

### Post by deviousdoses on 2009-02-28
I have latest ubuntu installed.  It comes with ieee80211 version 1.2.13

I can not install the latest ieee80211 version 1.2.18

After two weeks of research (yes two weeks!)  I am posting in hopes of someone knows the answer.

Been runing redhat for 11 years as dns/gateway with three nics, one going to network, and other two have different internet providers for redundancy.

I have compiled from source hundreds of times...



I can not however compile IEEE80211 (I'v trie 2.16, 2.17, and 1.2.18)

I've edited module.c to change proc_net to proc_init.proc.net, I've ran the apg-get install source, base, sharutils and all that.  I've even tried patching the thing first.

I can not make, or make install.

When I make, I get tons of errors, mainly about pro_net not defined.

What is going on here?  I've read Tons of posts here with similar probs and people are doing all sorts of things, I've tried them all and nothing works.


Has Anybody succesfully compiled IEEE80211 1.2.18 on latest Ubuntu?

If so, how?!?

Im about to throw a fit, after two of the most frustrating weeks in my computer.

---

