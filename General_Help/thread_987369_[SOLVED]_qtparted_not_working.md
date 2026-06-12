---
title: "[SOLVED] qtparted not working"
date: 2008-11-19
forum: General Help
---

### Post by peterroots on 2008-11-19
some time back I was able to use qtparted with kubuntu 7.04 7.10 and I think 8.04.  at some point qtparted stopped working i.e lots of bouncing cursor then no action of any sort.
Very annoying
The solution? I saw a posting about errors with gparted when run in terminal so thought 'I'll try that and see what errors I get' - answer, absolutely none as qtparted worked!!
The problem?
for some reason, best known to someone other than me, the Kubuntu menu had qtparted-root as the command and run as different user selected. changing the command to qtparted and leaving run as different user made all work again.

Really simple when you know how

---

### Post by iMacUser on 2009-05-22
Thanks peterroots, I was having the same trouble with qtparted (in Kubuntu 8.04) today and your post rescued me in one simple step.

---

