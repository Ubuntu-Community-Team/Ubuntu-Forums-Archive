---
title: "Will encrypting the home directory slow things down much?"
date: 2009-03-27
forum: Installation &amp; Upgrades
---

### Post by OsakaWilson on 2009-03-27
I'm now setting up Jaunty on my laptop. It is asking me if I want to encrypt my home directory. It sounds like a good idea. Will it cause a problem with speed?

---

### Post by tommcd on 2009-03-28
The answer seems to be yes, but probably not a whole lot. Here is an article with extensive benchmarking tests with encrypted and unencrypted partitions. The author concludes there will be a 5-10% performance penalty with encryption:
[http://www.fsckin.com/2008/01/15/howto-setup-and-benchmark-encrypted-partitions-in-ubuntu/](http://www.fsckin.com/2008/01/15/howto-setup-and-benchmark-encrypted-partitions-in-ubuntu/)
This article on Phoronix notes a performance drop with SSD drives as well for encryption:
[http://www.phoronix.com/scan.php?page=article&item=intel_atom_disk&num=1](http://www.phoronix.com/scan.php?page=article&item=intel_atom_disk&num=1)

If you are the sole user of the computer, or if you don't need to hide anything from people who may use the computer, then I would not worry about using encryption. I don't plan on using it.

---

