---
title: "Simple Intstall Question - Fresh install over exsisting Ubuntu install"
date: 2009-10-24
forum: Installation &amp; Upgrades
---

### Post by StuM on 2009-10-24
Hi,

Hopefully this is a simple question.  I recently mucked up my Karmic installation, and therefore decided to do a fresh install.  Except by doing so I now have 2 Ubuntu installs (and my Windows install) on the same disk.

I'm going to download the Karmic RC and want to keep my Windows install in tact, but delete / write over my two Ubuntu installs with a fresh Karmic RC one.  What is the easiest (i.e. least technical way) to do this?

Thanks

---

### Post by Bucky Ball on 2009-10-24
When you get to the partitioning section of the install choose 'Manual Partitioning'. You will see your Windows partition in there; just don't touch it. Delete the Ubuntu partitions and create new partitions, usually:

```
/
/home
/swap
```... at least but you can create what you want. A /boot partition is handy too and maybe one for music. The ones I've mentioned are defaults that you can select. Have a good look around in there.  Up to you and what space you have.

I have been assured that if you don't touch the existing /swap and /home by setting them to not reformat the new install will use them. I would do some research to prepare for manual partitioning and how to go about using some of the existing partitions if you want to go that way.

Good luck with it. Hope that helps.

---

### Post by StuM on 2009-10-24
Thanks... I got there in the end.  Fresh installed appears to have worked successfully.

---

