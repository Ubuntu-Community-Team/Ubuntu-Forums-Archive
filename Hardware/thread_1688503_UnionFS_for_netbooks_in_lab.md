---
title: "UnionFS for netbooks in lab"
date: 2011-02-15
forum: Hardware
---

### Post by jflash on 2011-02-15
Hey everyone,

I work for a school system, and we're looking at the possibility of using Netbook Remix on a batch of netbooks that we'll be deploying to some of our elementary students, primarily for use in a portable lab. We've done some looking at [Jim Klein's work]("http://community.saugususd.org/swattec/page/Linux+on+Netbooks") on a customised version, but have run into a few compatibility issues that don't seem to be present in the official release, so we're looking at essentially building our own custom installation. The biggest hurdle that I'm running into is implementing UnionFS in Ubuntu. I like the model of having a partition with a read-only base image and a read-write user space with the ability to quickly restore to the base image, and having the home directories on a separate read-write partition.

Can anyone provide some guidance on how best to implement this from a stock Netbook Remix installation?

Thanks in advance.

---

