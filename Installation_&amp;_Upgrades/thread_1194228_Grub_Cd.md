---
title: "Grub Cd??"
date: 2009-06-22
forum: Installation &amp; Upgrades
---

### Post by Spaceman7o on 2009-06-22
So ive just partitioned my drive and installed ubuntu using a cd after testing ubuntu with wubi now im scared because i completely ravaged my ubuntu on wubi which gave me a push start to partition my drive. So can anyone give me a link to the Grub Cd iso which i can burn to boot load if anything goes wrong, thanks.

---

### Post by Idefix82 on 2009-06-22
You will always be able to boot from the CD that you used to install Ubuntu, so no need to worry. Normally, this is the page you are looking for:
[http://www.supergrubdisk.org/]("http://www.supergrubdisk.org/") but it seems to be down at the moment.

---

### Post by Spaceman7o on 2009-06-22
> **Idefix82 said:**
> You will always be able to boot from the CD that you used to install Ubuntu, so no need to worry. Normally, this is the page you are looking for:
[http://www.supergrubdisk.org/](http://www.supergrubdisk.org/) but it seems to be down at the moment.

ok thankyou very much its just from that one experience i dont wana have to mess around i know i will be needing that cd sometime lol.

---

### Post by Idefix82 on 2009-06-22
It is useful sometimes, but not very often. As I said, you can always boot into the normal installation CD and do all the partitioning from there.

---

### Post by Mark Phelps on 2009-06-23
You specifically mentioned boot loading, so I'm guessing that what you really want is to be able to boot into Ubuntu.  If that's the case, the advice you've already been given regarding using the LiveCD is all that you need.

However, it's generally better to use a GParted LiveCD to do partitioning because (1) their version is newer than the ones bundled on the distros, and (2) their CD doesn't mount any partitions by default.  The second often goes unnoticed by folks using it for the first time when they don't understand that you can only do partitioning on an unmounted drive.

---

